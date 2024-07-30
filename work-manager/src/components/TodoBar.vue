<script setup>
	import { computed } from "vue";
	const props = defineProps({
		items: Array,
		warning: Number,
		dateType: String,
	});

	const todoItems = computed(() => props.items);
	const warningAmount = computed(() => props.warning);
	const dateType = computed(() => props.dateType);
	const importanceText = { 1: "Low", 2: "Medium", 3: "High" };
	const importanceColor = {
		1: "badge-success",
		2: "badge-warning",
		3: "badge-error",
	};

	function getCleanDate(date) {
		const dateObject = new Date(date);
		console.log(dateObject);

		const day = dateObject.getDate();
		const month = dateObject.getMonth() + 1;
		const year = dateObject.getFullYear();

		console.log(day);

		let cleanDate = "";
		let arrayDateType = [...dateType.value];
		console.log(arrayDateType);

		arrayDateType.forEach((e) => {
			switch (e) {
				case "D":
					cleanDate = cleanDate + day;
					break;
				case "M":
					cleanDate = cleanDate + month;
					break;
				case "Y":
					cleanDate = cleanDate + year;
					break;
				default:
					cleanDate = cleanDate + "/";
			}
		});
		return cleanDate;
	}

	function getDueDateColor(dueDate) {
		const currentDate = Date.now();
		const cleanDueDate = Date.parse(dueDate);

		let diffDate = currentDate - cleanDueDate;
		let diffDays = Math.round((diffDate / 86400000) * -1);

		// Return the result
		if (diffDays <= 0) {
			console.log(diffDays);
			return "badge-error";
		} else if (diffDays <= warningAmount.value) {
			console.log(diffDays);
			return "badge-warning";
		} else {
			console.log(warningAmount.value);

			console.log(diffDays);
			return "badge-outline";
		}
	}
	function getImportance(importance, isText) {
		if (isText == true) {
			return importanceText[importance];
		} else if (isText == false) {
			return importanceColor[importance];
		}
	}
</script>

<template>
	<div
		class="flex justify-center rounded-2xl bg-neutral max-w-96 flex-col"
		style="height: 90vh"
	>
		<div class="h-20 mb-8 mr-4 ml-4"></div>
		<div class="h-fit mb-8 mr-4 ml-4" style="height: 100%">
			<div
				class="card bg-base-100 w-full shadow-xl mb-2"
				v-for="(todo, index) in todoItems"
			>
				<div class="card-body">
					<div class="flex flex-row">
						<h3 class="card-title truncate">
							{{ todo.title }}
						</h3>
						<h3 class="card-title mr-2">...</h3>
					</div>
					<div class="card-actions justify-end">
						<div class="flex flex-col">
							<div class="badge mb-1" :class="getDueDateColor(todo.dueDate)">
								{{ getCleanDate(todo.dueDate) }}
							</div>
							<div class="badge" :class="getImportance(todo.importance, false)">
								{{ getImportance(todo.importance, true) }}
							</div>
						</div>
						<button class="btn btn-primary ml-auto">View</button>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<style scoped></style>

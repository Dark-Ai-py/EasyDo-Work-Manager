<script setup>
	const { todoItems } = defineProps(["items"]);
</script>

<template>
	<div
		class="flex justify-center rounded-2xl bg-neutral max-w-96 flex-col"
		style="height: 90vh"
	>
		<div class="outline-double outline-red-700 h-20 mb-8 mr-4 ml-4"></div>
		<div
			class="outline-double outline-blue-600 h-fit mb-8 mr-4 ml-4"
			style="height: 100%"
		>
			<div class="card bg-base-100 w-full shadow-xl mb-2">
				<div class="card-body">
					<h3 class="card-title truncate">
						Lorem ipsum dolor sit amet, consectetur adipisicing elit. Repellat
						culpa voluptatum, qui magni autem officiis at! Libero illum
						aspernatur labore, odit eius obcaecati voluptas alias vel eveniet
						aperiam cumque molestias.
					</h3>
					<h3 class="card-title truncate mr-2">...</h3>
					<div class="card-actions justify-end">
						<div class="badge badge-outline">Fashion</div>
						<div class="badge badge-outline">Products</div>
						<button class="btn btn-primary ml-auto">View</button>
					</div>
				</div>
			</div>
		</div>
	</div>
</template>

<style scoped></style>

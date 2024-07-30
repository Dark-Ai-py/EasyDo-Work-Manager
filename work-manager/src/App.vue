<script setup>
	import TodoBar from "./components/TodoBar.vue";
	let items = () => {
		//Test Set dont deploy to production
		return [
			{
				//UTC TIME
				dueDate: "Sun, 04 Aug 2024 05:00:00 GMT",
				title: "Finish ticket 624a3c",
				importance: "3",
			},
			{
				dueDate: "Fri, 08 Apr 2011 05:00:00 GMT",
				title: "Finish ticke... SAAAVEEE MMMEE---",
				importance: "2",
			},
		];
	};
</script>

<template>
	<!-- "items","warning","dateType", -->
	<TodoBar :items="items()" :warning="10" date-type="M-D-Y" />
</template>

<style scoped></style>

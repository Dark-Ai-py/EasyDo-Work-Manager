<script setup>
	const { todoItems } = defineProps(["items"]);
	function ParseProps() {}
</script>

<template>
	<div
		class="flex justify-center rounded-2xl bg-neutral max-w-80 flex-col"
		style="height: 80vh"
	>
		<div class="outline-double outline-red-700 h-20 mb-8 mr-4 ml-4"></div>
		<div
			class="outline-double outline-blue-600 h-fit mb-8 mr-4 ml-4"
			style="height: 100%"
		></div>
	</div>
</template>

<style scoped></style>

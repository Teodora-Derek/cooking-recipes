<script setup>
import { ref } from "vue";

const filter = ref("");

const emit = defineEmits(["filter-change"]);

const emitFilter = () => {
	emit("filter-change", filter.value);
};
</script>

<template>
	<input
		v-model="filter"
		@input="emitFilter"
		placeholder="Filter by recipe name"
	/>
</template>

<style>
/* Add filter input styles */
</style>

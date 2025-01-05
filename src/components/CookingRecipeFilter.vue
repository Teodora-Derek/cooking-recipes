<script setup>
import { defineModel } from "vue";
const filter = defineModel("filter");
</script>

<template>
	<input
		class="recipe-filter"
		v-model="filter"
		placeholder="Search recipes..."
	/>
</template>

<style></style>

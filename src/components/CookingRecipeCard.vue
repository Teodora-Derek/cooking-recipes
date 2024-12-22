<script setup>
const props = defineProps({
	recipe: {
		type: Object,
		required: true,
	},
});

const emit = defineEmits(["delete-recipe"]);

const deleteRecipe = () => {
	emit("delete-recipe");
};
</script>

<template>
	<div class="recipe-card">
		<img :src="recipe.imageSrc" :alt="recipe.name" />
		<h2>{{ recipe.name }}</h2>
		<p>{{ recipe.description }}</p>
		<button @click="deleteRecipe">Delete</button>
	</div>
</template>

<style>
/* Add card styles */
</style>

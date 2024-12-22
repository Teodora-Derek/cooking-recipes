<script setup>
import CookingRecipeCard from "./CookingRecipeCard.vue";
const props = defineProps({
	recipes: {
		type: Array,
		required: true,
	},
});

const emit = defineEmits(["delete-recipe"]);

const deleteRecipe = (index) => {
	emit("delete-recipe", index);
};
</script>

<template>
	<div class="recipe-list">
		<CookingRecipeCard
			v-for="(recipe, index) in recipes"
			:key="index"
			:recipe="recipe"
			@delete-recipe="deleteRecipe(index)"
		/>
	</div>
</template>

<style>
/* Add recipe list styles */
</style>

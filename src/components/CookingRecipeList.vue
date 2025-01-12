<script setup>
import CookingRecipeCard from "./CookingRecipeCard.vue";

const props = defineProps({
	recipes: {
		type: Array,
		required: true,
	},
});

const emit = defineEmits(["update-recipes"]);

const deleteRecipe = (id) => {
	emit("update-recipes", id);
};
</script>

<template>
	<div class="recipe-list">
		<CookingRecipeCard
			v-for="(recipe, index) in props.recipes"
			:key="index"
			:id="recipe.id"
			:name="recipe.name"
			:image="recipe.image"
			:ingredients="recipe.ingredients"
			:steps="recipe.steps"
			@delete-recipe="deleteRecipe"
		/>
	</div>
</template>

<style scoped>
.recipe-list {
	display: flex;
	flex-wrap: wrap;
	gap: 20px;
	justify-content: center;
}
</style>

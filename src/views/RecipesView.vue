<script setup lang="js">
import { ref, onMounted, computed } from "vue";
import CookingRecipeFilter from "../components/CookingRecipeFilter.vue";
import CookingRecipeList from "../components/CookingRecipeList.vue";

const filter = ref('');
const recipes = ref([]);
const isLoading = ref(true);

const fetchRecipes = async () => {
  try {
    const savedRecipes = localStorage.getItem("recipes");
	  if (savedRecipes) {
      recipes.value = JSON.parse(savedRecipes);
	  } else {
      const response = await fetch("/recipes.json");
      recipes.value = await response.json();
	  }
  } catch (error) {
    console.error("Failed to load recipes:", error);
  } finally {
    isLoading.value = false;
  }
};

const updateRecipes = (newRecipes) => {
  recipes.value = newRecipes;
  localStorage.setItem("recipes", JSON.stringify(recipes.value));
};

onMounted(fetchRecipes);

const recipesFiltered = computed(() => {
  const search = filter.value.trim().toLowerCase();
  return recipes.value.filter(recipe =>
    recipe.name.toLowerCase().includes(search)
  );
});
</script>

<template>
	<div>
		<h2>Recipes</h2>
		<div>
			<CookingRecipeFilter v-model:filter="filter" />
		</div>
		<div v-if="isLoading">Loading...</div>
		<div v-else-if="!recipesFiltered.length">
			<h2>No recipes available</h2>
		</div>
		<div v-else>
			<CookingRecipeList
				:recipes="recipesFiltered"
				@update-recipes="updateRecipes"
			/>
		</div>
	</div>
</template>

<style scoped>
h2 {
  margin: 0 1rem 0 1rem;
}
</style>

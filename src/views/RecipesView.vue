<script setup lang="js">
import { ref, onMounted, computed } from "vue";
import CookingRecipeFilter from "../components/CookingRecipeFilter.vue";
import CookingRecipeList from "../components/CookingRecipeList.vue";
import AddCookingRecipe from "@/components/AddCookingRecipe.vue";

const showRecipes = ref(true);
const filter = ref('');
const recipes = ref([]);
const isLoading = ref(true);

const fetchRecipes = async () => {
  try {
    const response = await fetch("/recipes.json");
    recipes.value = await response.json();
  } catch (error) {
    console.error("Failed to load recipes:", error);
  } finally {
    isLoading.value = false;
  }
};

const deleteRecipe = (id) => {
	recipes.value = recipes.value.filter(
		(recipe) => recipe.id !== id
	);
};

onMounted(fetchRecipes);

const recipesFiltered = computed(() => {
  const search = filter.value.trim().toLowerCase();

  if(search == '') {
	  return recipes.value;
  }

  return recipes.value.filter(recipe =>
    recipe.name.toLowerCase().includes(search)
  );
});

const addNewRecipe = (recipe) => {
	recipe.id = recipes.value.length + 1;
	recipes.value.push(recipe);
	showRecipes.value = true;
}
</script>

<template>
	<div>
		<div v-if="showRecipes">
			<div class="navigationBtnWrapper listFormated">
				<button class="navigationBtn" @click="showRecipes = false">
					Add new recipe
				</button>
			</div>
			<div>
				<CookingRecipeFilter v-model:filter="filter" />
			</div>
			<div v-if="isLoading">Loading...</div>
			<div v-else-if="recipes.length == 0">
				<h2>No recipes available</h2>
			</div>
			<div v-else>
				<CookingRecipeList
					:recipes="recipesFiltered"
					@update-recipes="deleteRecipe"
				/>
			</div>
		</div>
		<div v-else>
			<div class="navigationBtnWrapper listFormated">
				<button class="navigationBtn" @click="showRecipes = true">
					Back
				</button>
			</div>
			<AddCookingRecipe @add-recipe="addNewRecipe" />
		</div>
	</div>
</template>

<style scoped>
.navigationBtnWrapper {
	position: relative;
	min-height: 2.5em;
}

.navigationBtn {
	position: absolute;
	top: 0;
	right: 0;
	width: 15%;
	min-width: fit-content;
	min-height: fit-content;
}

.listFormated {
	margin: 0 1rem 0 1rem;
}
</style>

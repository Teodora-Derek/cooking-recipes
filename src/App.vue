<script setup>
import { ref, computed } from "vue";
import { RouterLink, RouterView } from "vue-router";
// import AddCookingRecipe from "./components/AddCookingRecipe.vue";
// import CookingRecipeFilter from "./components/CookingRecipeFilter.vue";
// import CookingRecipeList from "./components/CookingRecipeList.vue";

// const recipes = ref([]);
// const filterText = ref("");

// const addRecipe = (recipe) => {
// 	recipes.value.push(recipe);
// };

// const deleteRecipe = (index) => {
// 	recipes.value.splice(index, 1);
// };

// const setFilter = (filter) => {
// 	filterText.value = filter;
// };

// const filteredRecipes = computed(() =>
// 	recipes.value.filter((recipe) =>
// 		recipe.name.toLowerCase().includes(filterText.value.toLowerCase())
// 	)
// );
</script>

<template>
	<div class="app">
		<header>
			<img
				alt="Cooking recipe manager logo"
				class="logo"
				src="@/assets/logo.svg"
				width="125"
				height="125"
			/>
			<h1>Cooking Recipe Manager</h1>
			<div class="wrapper">
				<nav>
					<RouterLink to="/">Home</RouterLink>
					<RouterLink to="/about">About</RouterLink>
				</nav>
			</div>
		</header>
		<!-- <AddCookingRecipe @add-recipe="addRecipe" />
		<CookingRecipeFilter @filter-change="setFilter" />
		<CookingRecipeList
			:recipes="filteredRecipes"
			@delete-recipe="deleteRecipe"
		/> -->
		<main class="content">
			<RouterView />
		</main>
	</div>
</template>

<!-- <style scoped>
body {
	background-color: beige;
}

header {
	line-height: 1.5;
	max-height: 100vh;
	background-color: var(
		--color-background,
		#faf8f8
	); /* Optional background for header */
	background-color: beige;
	padding: 1rem;
	text-align: center;
	box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
	z-index: 1; /* Keep header above other content */
}

main {
	background-color: beige;
}

.logo {
	display: block;
	margin: 0 auto 1rem;
	background-color: beige;
}

nav {
	display: flex;
	justify-content: center; /* Center the links horizontally */
	align-items: center;
	gap: 1rem; /* Add spacing between links */
	background-color: #007bff; /* Blue background color for nav */
	padding: 0.5rem 1rem;
	border-radius: 8px; /* Rounded corners for the nav background */
	box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1); /* Subtle shadow for depth */
}

nav a {
	color: #fff; /* White text color */
	text-decoration: none; /* Remove underline */
	padding: 0.5rem 1rem; /* Add padding around links */
	border-radius: 4px; /* Rounded corners for individual links */
	transition: background-color 0.3s, color 0.3s; /* Smooth hover effect */
	font-size: 1rem; /* Font size for links */
}

nav a:hover {
	background-color: #0056b3; /* Darker blue on hover */
	color: #f8f9fa; /* Optional lighter text color on hover */
}

nav a.router-link-exact-active {
	background-color: #0056b3; /* Highlight active link */
	font-weight: bold; /* Bold text for active link */
}

/* Scrollable main content */
.content {
  flex: 1; /* Allow content to grow and take available space */
  overflow-y: auto; /* Enable vertical scrolling for content */
  padding: 1rem;
  background-color: var(--color-content-bg, #f9f9f9);
  box-sizing: border-box;
}
</style> -->

<style>
.app {
	min-height: 100vh; /* Ensure the page takes at least the full viewport height */
	display: flex;
	flex-direction: column;
}

header {
	background-color: var(--color-background, beige);
	padding: 1rem;
	text-align: center;
	box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

.logo {
	display: block;
	margin: 0 auto 1rem;
}

nav {
	display: flex;
	justify-content: center;
	gap: 1rem;
	background-color: #007bff;
	padding: 0.5rem 1rem;
	border-radius: 8px;
	box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
}

nav a {
	color: #fff;
	text-decoration: none;
	padding: 0.5rem 1rem;
	border-radius: 4px;
	transition: background-color 0.3s, color 0.3s;
}

nav a:hover {
	background-color: #0056b3;
	color: #f8f9fa;
}

nav a.router-link-exact-active {
	background-color: #0056b3;
	font-weight: bold;
}

/* Content section */
.content {
	flex: 1; /* Allow content to grow and push footer to the bottom */
	padding: 1rem;
	background-color: var(--color-content-bg, #f9f9f9);
}

/* Allow page scrolling */
body {
	margin: 0;
	padding: 0;
	box-sizing: border-box;
	font-family: Arial, sans-serif;
	background-color: #f9f9f9;
}

html,
body {
	height: 100%; /* Ensure body takes full height */
	overflow-y: auto; /* Allow scrolling for the entire page */
}
</style>

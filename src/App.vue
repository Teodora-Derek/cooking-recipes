<script setup>
import { RouterLink, RouterView } from "vue-router";
</script>

<template>
	<div class="app">
		<header>
			<img
				alt="Cooking recipes manager logo"
				class="logo"
				src="/recipe.ico"
				width="125"
				height="125"
			/>
			<h1>Cooking recipes manager</h1>
			<div class="wrapper">
				<nav>
					<RouterLink to="/">Home</RouterLink>
					<RouterLink to="/recipes">Recipes</RouterLink>
				</nav>
			</div>
		</header>
		<main class="content">
			<RouterView />
		</main>
	</div>
</template>

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
	margin: 0 auto 0;
}

h1 {
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

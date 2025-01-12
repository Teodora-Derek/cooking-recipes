<script setup>
import { reactive } from "vue";

const emit = defineEmits(["add-recipe"]);

const form = reactive({
	name: "",
	image: "",
	ingredients: "",
	steps: "",
});

const submitRecipe = () => {
	const newRecipe = {
		name: form.name,
		image: form.image,
		ingredients: form.ingredients.split(",").map((item) => item.trim()),
		steps: form.steps.split(",").map((item) => item.trim()),
	};

	emit("add-recipe", newRecipe);

	form.name = "";
	form.image = "";
	form.ingredients = "";
	form.steps = "";
};
</script>

<template>
	<form @submit.prevent="submitRecipe">
		<div>
			<label for="name">Recipe Name:</label>
			<input v-model="form.name" id="name" required />
		</div>
		<div>
			<label for="image">Image URL:</label>
			<input v-model="form.image" id="image" required />
		</div>
		<div>
			<label for="ingredients">Ingredients (comma-separated):</label>
			<input v-model="form.ingredients" id="ingredients" required />
		</div>
		<div>
			<label for="steps">Steps (comma-separated):</label>
			<input v-model="form.steps" id="steps" required />
		</div>
		<button type="submit">Add Recipe</button>
	</form>
</template>

<style>
form {
	border-radius: 10px;
}

form input {
	border-radius: 5px;
	border-width: thin;
}

form textarea {
	overflow: auto;
	max-width: 100%;
	min-width: 100%;
	min-height: 3rem;
	max-height: 20rem;
	border-radius: 5px;
}

form button {
	background-color: #04AA6D;
	margin: 0;
}

form button:hover {
	background-color: #059862 ;
}
</style>

<script setup>
import { ref } from "vue";

const name = ref("");
const image = ref("");
const ingredients = ref([]);
const steps = ref([]);

const emit = defineEmits(["add-recipe"]);

const submitForm = () => {
	if (name.value && image.value && ingredients.value && steps.value) {
		emit("add-recipe", {
			name: name.value,
			image: image.value,
			ingredients: ingredients.value,
			steps: steps.value,
		});
		name.value = "";
		image.value = "";
		ingredients.value = [];
		steps.value = [];
	}
};
</script>

<template>
	<form @submit.prevent="submitForm">
		<input v-model="name" placeholder="Recipe Name" required />
		<input v-model="image" placeholder="Image URL" required />
		<textarea
			v-model="ingredients"
			placeholder="Ingredients"
			required
		></textarea>
		<textarea v-model="steps" placeholder="Steps" required></textarea>
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

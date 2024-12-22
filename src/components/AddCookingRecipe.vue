<script setup>
import { ref } from "vue";

const name = ref("");
const imageSrc = ref("");
const description = ref("");

const emit = defineEmits(["add-recipe"]);

const submitForm = () => {
	if (name.value && imageSrc.value && description.value) {
		emit("add-recipe", {
			name: name.value,
			imageSrc: imageSrc.value,
			description: description.value,
		});
		name.value = "";
		imageSrc.value = "";
		description.value = "";
	}
};
</script>

<template>
	<form @submit.prevent="submitForm">
		<input v-model="name" placeholder="Recipe Name" required />
		<input v-model="imageSrc" placeholder="Image URL" required />
		<textarea
			v-model="description"
			placeholder="Description"
			required
		></textarea>
		<button type="submit">Add Recipe</button>
	</form>
</template>

<style>
/* Add form-specific styles */
</style>

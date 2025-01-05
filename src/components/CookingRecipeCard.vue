<script setup>
const props = defineProps({
	id: {
      type: Number,
      required: true,
    },
    name: {
      type: String,
      required: true,
    },
    image: {
      type: String,
      required: true,
    },
    ingredients: {
      type: Array,
      required: true,
    },
    steps: {
      type: Array,
      required: true,
    }
});

const emit = defineEmits(["delete-recipe"]);

const deleteRecipe = (id) => {
	emit("delete-recipe", id);
};
</script>

<template>
	<div class="recipe-card">
		<img :src="image" :alt="name" />
		<h2>{{ name }}</h2>
		<p><strong>Ingredients:</strong></p>
		<ul>
			<li v-for="(ingredient, idx) in ingredients" :key="idx">
				{{ ingredient }}
			</li>
		</ul>
		<p><strong>Description:</strong></p>
		<ol>
			<li v-for="(step, idx) in steps" :key="idx">
				{{ step }}
			</li>
		</ol>
		<button @click="deleteRecipe(id)">Delete</button>
	</div>
</template>

<style>
.recipe-card {
	border: 1px solid #ddd;
	border-radius: 8px;
	padding: 16px;
	background-color: #fff;
	max-width: 300px;
	box-shadow: 0 4px 6px rgba(0, 0, 0, 0.1);
	text-align: center;
	transition: transform 0.2s ease, box-shadow 0.2s ease;
}

.recipe-card:hover {
	transform: scale(1.05);
	box-shadow: 0 6px 10px rgba(0, 0, 0, 0.15);
}

.recipe-card img {
	width: 100%;
	height: auto;
	border-radius: 4px;
}

.recipe-card h2 {
	font-size: 1.5rem;
	margin: 12px 0;
}

.recipe-card ul,
.recipe-card ol {
	text-align: left;
	margin: 0 0 12px;
	padding-left: 20px;
}

.recipe-card button {
	background-color: #e74c3c;
	color: #fff;
	border: none;
	padding: 10px 16px;
	border-radius: 4px;
	cursor: pointer;
	transition: background-color 0.3s ease;
}

.recipe-card button:hover {
	background-color: #c0392b;
}
</style>

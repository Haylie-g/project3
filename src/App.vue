<script setup>
import { ref } from 'vue';

const recipeName = ref('');
const ingredients = ref('');
const directions = ref('');
const generatedRecipe = ref(null);

const generateRecipe = () => {
  // Check if the recipe name is provided
  if (!recipeName.value.trim()) {
    // Handle the case where the recipe name is missing
    alert('Please enter a recipe name.');
    return;
  }

  // Generate the recipe object
  generatedRecipe.value = {
    name: recipeName.value,
    ingredients: ingredients.value,
    directions: directions.value,
  };
};
</script>

<template>
 <div>
    <header>
      <h1>Recipe Maker &#127856;</h1>
    </header>

    <main>
      <section id="recipe-input">
        <h2>Enter Your Recipe</h2>
        <form @submit.prevent="generateRecipe">
          <fieldset>
            <legend>Recipe Name</legend>
            <input v-model="recipeName" type="text" placeholder="Enter recipe name..." required>
          </fieldset>

          <fieldset>
            <legend>Ingredients</legend>
            <textarea v-model="ingredients" rows="5" cols="50" placeholder="Enter ingredients here..." required></textarea>
          </fieldset>

          <fieldset>
            <legend>Directions</legend>
            <textarea v-model="directions" rows="5" cols="50" placeholder="Enter directions here..." required></textarea>
          </fieldset>

          <button type="submit">Generate Recipe</button>
        </form>

      </section>

      <section id="recipe-output">
        <h2>Your Recipe</h2>
        <div v-if="generatedRecipe">
          <h3>{{ generatedRecipe.name }}</h3>
          <p><strong>Ingredients:</strong></p>
          <p>{{ generatedRecipe.ingredients }}</p>
          <p><strong>Directions:</strong></p>
          <p>{{ generatedRecipe.directions }}</p>
        </div>
      </section>
    </main>
 </div>
 </template>






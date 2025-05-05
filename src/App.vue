<template>
<div class="container">
  <h1>Recipes</h1>
  <CategoryList @search="handleSearch"/>
  <SearchBar @search="handleSearch" />
  <div v-if="searchResults?.length">
    <h2>Sökresultat</h2>
    <div class="grid">
        <RecipeCard v-for="meal in searchResults" :key="meal.idMeal" :meal="meal"/> 
    </div>
  </div>
  <p v-else-if="searched">No results found</p>
  </div>
  <RandomRecipes />

</template>

<script setup>
import SearchBar from './components/SearchBarComponent.vue'
import RandomRecipes from './components/RandomRecipes.vue';
import CategoryList from './components/CategoryList.vue';
import RecipeCard from './components/RecipeCard.vue';
import { ref } from 'vue';

const searchResults= ref([]);
const searched=ref(false);

async function handleSearch(query){
  searched.value=true//?
  const res = await fetch(`https://www.themealdb.com/api/json/v1/1/search.php?s=${query}`)
  const data = await res.json()
  searchResults.value=data.meals || []
}

</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.container {
  font-family: Arial, sans-serif;
  padding: 1rem;
}
.grid {
  display: flex;
  flex-wrap: wrap;
  gap: 1rem;
  justify-content: center;
}
</style>

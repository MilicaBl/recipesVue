<template>
    <div class="card">
        <img :src="meal.strMealThumb" :alt="meal.strNeal" />
        <h3>{{ meal.strMeal }}</h3>
        <p>{{ meal.strInstructions.slice(0, 100) }}...</p>
    </div>
</template>

<script setup>
import { defineProps } from 'vue';
defineProps(['meal'])
</script >

<style scoped>
.card {
  width: 250px;
  border: 1px solid #ccc;
  padding: 1rem;
  border-radius: 8px;
  background-color: rgb(197, 215, 215);
}
img {
  width: 100%;
  border-radius: 8px;
}
</style>
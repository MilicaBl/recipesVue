<template>
    <div>
        <h2>Random recipes </h2>
        <div class="grid">
            <RecipeCard v-for="meal in randomMeals" :key="meal.idMeal" :meal="meal"/>
        </div>
    </div>
</template>

<script setup>
import { onMounted, ref } from 'vue';
import RecipeCard from './RecipeCard.vue';

const randomMeals= ref([])

async function fetchRandomMeals(){
    const promises = Array.from({length:9}, ()=>
        fetch('https://www.themealdb.com/api/json/v1/1/random.php').then(res=> res.json())
    )

    const results = await Promise.all(promises)
    randomMeals.value=results.map(r => r.meals[0])
}
 onMounted(fetchRandomMeals)
</script>

<style scoped>
.grid {
  display: flex;
  gap: 1rem;
  margin-bottom: 2rem;
}
</style>
<template>
    <h2>Categories</h2>
    <div class="category-list">
        <span v-for="cat in categories" :key="cat.strCategory" class="chip" @click="emitCategory(cat.strCategory)">
            {{ cat.strCategory }}
        </span>
    </div>
</template>

<script setup>
import { onMounted, ref, defineEmits} from 'vue';

const categories= ref([])
const emit= defineEmits(['search'])
function emitCategory(category){
    console.log(category);
    
    emit('search', category)
}
async function fetchCategories() {
    const res = await fetch('https://www.themealdb.com/api/json/v1/1/categories.php')
    const data =await res.json()
    categories.value=data.categories
}
onMounted(fetchCategories)
</script>

<style scoped>
.category-list {
  display: flex;
  justify-content: center;
  flex-wrap: wrap;
  gap: 0.5rem;
  margin-bottom: 2rem;
}
.chip {
  background: #eee;
  padding: 0.4rem 0.8rem;
  border-radius: 999px;
  cursor: pointer;
}
.chip:hover{
    background-color: rgb(197, 215, 215);
}
</style>
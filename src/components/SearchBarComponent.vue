<template>
    <div class="search">
        <input v-model="query" placeholder="Search recipes..." /> 
        <button @click="emitSearch">Search</button>
    </div>

</template>

<script setup>
import { ref, defineEmits } from 'vue';

const query= ref('')
const emit= defineEmits(['search'])

function emitSearch(){
    if(query.value.trim()) emit('search', query.value.trim())
}

</script>

<style scoped>
.search {
  margin-bottom: 1rem;
}
input {
  padding: 0.5rem;
  width: 200px;
}
button {
  margin-left: 0.5rem;
  padding: 0.5rem 1rem;
}
</style>
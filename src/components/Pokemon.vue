<template>
<h1>Pokemons</h1>
<div v-if="pokemon.name != null" style="margin-bottom:20px; border: 1px solid black">
    Name:{{ pokemon.name }}<br/>
    Weight: {{ pokemon.weight }}
</div>
<div>
    <a v-for="pokemon in pokemons" :key="pokemon.name" @click="getPokemon(pokemon.url)">{{ pokemon.name }}<br/></a>
</div>

</template>
<script>
 export default{
    name:"PokemonCard",
    data(){
        return{
            pokemons:[],
            pokemon:{}
        }
    },
    created(){
        console.log("Created");
        fetch("https://pokeapi.co/api/v2/pokemon")
        .then(res=>res.json())
        .then(data=> {
            console.log(data.results)
            this.pokemons= data.results;
    })
        
    },
    mounted(){
        console.log("Mounted");
        
    },
    updated(){
        console.log("Updated");
        
    },
    methods:{
        getPokemon(url){
            fetch(url)
            .then(res=>res.json())
            .then(data=>{
                console.log(data)
                this.pokemon=data
            })
        }
    }
 }
</script>
<style>
</style>
<template>
  <form @submit="handleSubmit">
   Förnamn:  <input type="text" v-model="localUser.userName" id="firstName"/><br/>
   Efternamn:  <input type="text" v-model="localUser.lastName" id="lastName"/><br/>
    <button>Spara</button>
  </form>
</template>
<script>
export default{
    name:"UserForm",
    props: {
        user: {
            type:Object,
        }
    },
    data() {
    return {
      localUser: { ...this.user }  // skapar en lokal kopia
    };
  },
  methods:{
    handleSubmit(e){
        this.$emit("save", e)
    }
  }
}
</script>
<style>
</style>
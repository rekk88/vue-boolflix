<template>
  <div class="header_wrapper container-fluid d-flex justify-content-center align-items-center">
      <input type="text" placeholder="inserisci un titolo" class="mx-2">
      <button type="button" class="btn btn-secondary" @click="getFilms">Cerca</button>
  </div>
</template>

<script>
export default {
    name:"Header",
    components:{

    },
    data() {
        return {
            
        }
    },
    methods:{
        getFilms(){
            console.log("ciao");
        }
    }
}
</script>

<style lang="scss" scoped>
    .header_wrapper{
        height: 70px;
        background: #2c3e50;
        input{
            height: 2rem;
        }

    }
</style>
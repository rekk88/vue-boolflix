<template>
  <div class="header_wrapper container-fluid d-flex justify-content-center align-items-center">
      <input type="text" placeholder="inserisci un titolo"  v-model="francesco" class="mx-2">
      <button type="button" class="btn btn-secondary" @click="getFilms">Cerca</button>
  </div>
</template>

<script>
import axios from 'axios';

export default {
    name:"Header",
    components:{

    },
    data() {
        return {
            francesco:"",
            url: "https://api.themoviedb.org/3/search/movie?api_key=75ebf4a5bf0762d3887d0146d0d76336&query=",

        }
    },
    methods:{
        getFilms(){
            console.log("ciao");
            this.url = this.url + this.francesco;
            axios
                .get(this.url)
                .then(response =>{
                    console.log(response);
                })
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
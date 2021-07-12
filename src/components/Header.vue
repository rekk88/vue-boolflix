<template>
  <div class="header_wrapper container-fluid d-flex justify-content-center align-items-center">
      <input type="text" placeholder="inserisci un titolo"  v-model="ricerca" class="mx-2">
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
            ricerca:"",
            page:"1",
            url: "https://api.themoviedb.org/3/search/movie?api_key=75ebf4a5bf0762d3887d0146d0d76336&query=",
            films : "",
        }
    },
    methods:{
        getFilms(){
            console.log("ciao");
            this.films="";
            // console.log("text ricerca : ",this.ricerca);
            this.url = this.url + this.ricerca;
            // console.log("url get : ",this.url);
            axios
                .get(this.url)
                .then(response =>{
                    console.log(response);
                    console.log(response.data.total_pages);
                    console.log(response.data.results.length);
                    console.log(response.data.results[0]);
                    this.films=response.data.results;
                    // console.log(this.films.title);s
                    // console.log("films :  ",this.films);
                    
                })
            this.ricerca="";
            this.url="https://api.themoviedb.org/3/search/movie?api_key=75ebf4a5bf0762d3887d0146d0d76336&query=";
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
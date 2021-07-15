<template>
  <div id="app">
    <Header @getFilmsEmit="getFilms" @getTvEmit="getTV"/>
    <Main :film="films" :series="series"/>
  </div>
</template>

<script>
import Header from './components/Header.vue'
import Main from './components/Main.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    Header,
    Main

  },
  data() {
    return {
      page:"1",
      urlFilm: "https://api.themoviedb.org/3/search/movie?api_key=75ebf4a5bf0762d3887d0146d0d76336&query=",
      films : [],
      urlTV:"https://api.themoviedb.org/3/search/tv?api_key=75ebf4a5bf0762d3887d0146d0d76336&query=",
      series:[]
    }
  },
  methods:{
      getFilms(ricerca){
            console.log("Film");
            this.urlFilm = this.urlFilm + ricerca;
            axios
                .get(this.urlFilm)
                .then(response =>{
                    this.films=response.data.results;
                    console.log("film : ",this.films);
                })
            //reset variabili di ricerca e urlFilm
            this.ricerca="";
            this.urlFilm="https://api.themoviedb.org/3/search/movie?api_key=75ebf4a5bf0762d3887d0146d0d76336&query=";

        },
      getTV(ricerca){
        console.log("serieTV");
        this.urlTV = this.urlTV + ricerca;
        axios
          .get(this.urlTV)
          .then(response =>{
              this.series = response.data.results;
              console.log(this.series);

          })
        this.ricerca="";
        this.urlTV="https://api.themoviedb.org/3/search/tv?api_key=75ebf4a5bf0762d3887d0146d0d76336&query=";
        
      }
  }
}
</script>

<style lang="scss">
@import "./style/commons.scss";
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
}
</style>

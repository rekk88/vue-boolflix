<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png">
    <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <Header @getFilmsEmit="getFilms"/>
    <Main :film="films"/>
  </div>
</template>

<script>
// import HelloWorld from './components/HelloWorld.vue'
import Header from './components/Header.vue'
import Main from './components/Main.vue'
import axios from 'axios'

export default {
  name: 'App',
  components: {
    // HelloWorld
    Header,
    Main

  },
  data() {
    return {
      page:"1",
      url: "https://api.themoviedb.org/3/search/movie?api_key=75ebf4a5bf0762d3887d0146d0d76336&query=",
      films : "",
    }
  },
  methods:{
     getFilms(ricerca){
            console.log("ciao");
            // console.log("text ricerca : ",this.ricerca);
            this.url = this.url + ricerca;
            // console.log("url get : ",this.url);
            axios
                .get(this.url)
                .then(response =>{
                  
                    this.films=response.data.results;
                    console.log(this.films);
                    
                })
            //reset variabili di ricerca e url
            this.ricerca="";
            this.url="https://api.themoviedb.org/3/search/movie?api_key=75ebf4a5bf0762d3887d0146d0d76336&query=";

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
  color: #2c3e50;
}
</style>

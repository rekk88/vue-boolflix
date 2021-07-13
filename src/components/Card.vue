<template>
  <div class="card_wrapper">
      <ul>
        <li ></li>
      </ul>
  </div>
</template>

<script>
import {eventBus} from '../main.js'

export default {
    name:'Cards',
    data() {
      return {
        filmCard : "",
      }
    },
    mounted(){
    },
    methods:{
      getFilm(){
        eventBus.$on('bus', element => {
          this.filmCard = element;
        });
        console.log(this.filmCard);
      }
    }
    
}



</script>

<style lang="scss" scoped>

</style>
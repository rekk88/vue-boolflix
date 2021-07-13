<template>
  <div class="card_wrapper">
      <ul>
        <li>
          <div>titolo : {{francesco.title}}</div>
          <div>titolo originale: {{francesco.original_title}}</div>
          <div> <img :src=path alt="immagine"></div>
          <div>voto : {{francesco.vote_average}}</div>
          <!-- <div><img src="https://www.countryflags.io/be/flat/64.png" alt="flag"></div> -->
        </li>
      </ul>
  </div>
</template>

<script>

export default {
    name:'Cards',
    data() {
      return {
        path : require('@/assets/images/'+this.francesco.original_language+'.png')
      }
    },
    props:{
      francesco : Object
    },
    // mounted(){
    //   this.$nextTick(this.getFilm())
    // },
    updated(){
    },
    methods:{

    }
    
}



</script>

<style lang="scss" scoped>
  ul{
    li {
      list-style: none;
    }
  }
</style>
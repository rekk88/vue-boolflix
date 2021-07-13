<template>
  <div class="card_wrapper">
      <ul>
        <li>
          <div>titolo : {{film2.title}}</div>
          <div>titolo originale: {{film2.original_title}}</div>
          <div> <img :src=path alt="immagine"></div>
          <div>voto : {{film2.vote_average}}</div>
          <!-- <div><img src="https://www.countryflags.io/be/flat/64.png" alt="flag"></div> -->
        </li>
      </ul>
      <ul>
        <li>
          <!-- <div>titolo : {{series.title}}</div> -->
          <div>titolo originale: {{series.original_name}}</div>
          <div> <img :src=path alt="immagine"></div>
          <div>voto : {{series.vote_average}}</div>
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
        path : require('@/assets/images/'+this.film2.original_language+'.png')
      }
    },
    props:{
      film2 : Object,
      series : Object
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
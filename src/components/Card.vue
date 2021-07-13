<template>
  <div class="card_wrapper">
      <ul>
        <li>
          <div>titolo : {{francesco.title}}</div>
          <div>titolo originale: {{francesco.original_title}}</div>
          <div>lingua originale : {{francesco.original_language}} <img :src="'../assets/images/'+francesco.original_language+'.png'" alt="immagine"></div>
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
        flags :[
          {
            language : "en",
            flag:"",
          },
          // {
          //   language : "",
          //   flag:"",
          // },
          // {
          //   language : "",
          //   flag:"",
          // },
        ]
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
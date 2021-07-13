<template>
  <div class="card_wrapper">
        <li>
          <div>{{ type }}</div>
           <div>titolo originale: {{title}}</div> 
           <div> <img :src=path alt="immagine"></div> 
           <div>voto : {{voto}}</div> 
        </li>      
  </div>
  
</template>

<script>

export default {
    name:'Cards',
    data() {
      return {
        path : require('@/assets/images/'+this.originalLanguage+'.png')
      }
    },
    props:{
      originalLanguage:String,
      title : String,
      voto: Number,
      type: String
    },
    methods:{

    }
    
}



</script>

<style lang="scss" scoped>
    li {
      list-style: none;
    }
</style>
<template>
  <div class="card_wrapper">
        <li>
          <div><img :src=locandina alt="Immagine non disponibile"></div>
          <div>{{ type }}</div>
          <div>titolo : {{title}}</div> 
          <div v-if="originalTitle != title">titolo originale : {{originalTitle}}</div>
          <div> <img :src=path alt="immagine"></div> 
          <div>voto : {{calcoloVoto(voto)}} 
            <i v-for="index in calcoloVoto(voto)" :key="index" class="fas fa-star"></i>
            <i v-for="index in (5-calcoloVoto(voto))" :key="index" class="far fa-star"></i>
          </div> 
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
      originalTitle: String,
      voto: Number,
      type: String,
      locandina:String
    },
    methods:{
      calcoloVoto(voto){
        // console.log("voto :" , voto);
        return Math.round(voto / 2)
      }
    },
    
}



</script>

<style lang="scss" scoped>
    li {
      list-style: none;
    }
</style>
<template>
  <div class="card_wrapper col" v-if="(path != null) && (title != null)">
    <div class="card">
          <img class="card-img-top" :src=locandina alt="Immagine non disponibile">
          <div class="card-body">
            <div>{{ type }}</div>
            <div>titolo : {{title}}</div> 
            <div v-if="originalTitle != title">titolo originale : {{originalTitle}}</div>
            <div> <img :src="require('@/assets/images/'+this.originalLanguage+'.png')" alt="immagine"></div> 
            <div>
              voto : {{calcoloVoto(voto)}} 
              <i v-for="index in calcoloVoto(voto)" :key="index" class="fas fa-star"></i>
              <i v-for="index in (5-calcoloVoto(voto))" :key="index" class="far fa-star"></i>
            </div>
          </div>
    </div>    
  </div>
  
</template>

<script>

export default {
    name:'Cards',
    data() {
      return {
      }
    },
    props:{
      originalLanguage:String,
      title : String,
      originalTitle: String,
      voto: Number,
      popularity:Number,
      type: String,
      locandina:String,
      path:String
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
.card-body{
  // display: none;
  visibility: hidden;
  position: absolute;
  top: 0;
  width:100%;
  height: 100%;
  background-color: black;
  opacity: 0;
  transition: linear .2s;
}

.card{
  height: 100%;
  &:hover{
    .card-body{
      visibility:visible;
      opacity: 0.8;
    }
  }
  .card-img-top{
    height: 100%;
  }
}
</style>
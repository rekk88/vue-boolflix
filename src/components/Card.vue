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
              <!-- voto : {{calcoloVoto(voto)}}  -->
              <i v-for="index in calcoloVoto(voto)" :key="index" class="fas fa-star"></i>
              <i v-for="index in (5-calcoloVoto(voto))" :key="index" class="far fa-star"></i>
            </div>
            <div>
              {{idProva}}  <!--debug-->
              {{descrizione}}
            </div>
            <div v-if="cast.length > 0"><h4 class="mt-2">Cast</h4></div>
            <div class="cast" v-for="(p,index) in cast.slice(0 , 5)" :key="index">

              {{p.name}}
            </div>
          </div>
    </div>    
  </div>
  
</template>

<script>
import axios from 'axios';

export default {
    name:'Cards',
    data() {
      return {
        idProva : this.id,
        cast : "",
      }
    },
    props:{
      id : Number, 
      originalLanguage: String,
      title : String,
      originalTitle: String,
      descrizione : String,
      voto: Number,
      popularity:Number,
      type: String,
      locandina: String,
      path: String
    },
    methods:{
      calcoloVoto(voto){
        // console.log("voto :" , voto);
        return Math.round(voto / 2)
      },
    },

    mounted(){
      let urlCast = "https://api.themoviedb.org/3/"+this.type+"/"+this.id+"/credits?api_key=75ebf4a5bf0762d3887d0146d0d76336"
      console.log(urlCast);
      axios
        .get(urlCast)
        .then(response =>{
          console.log(response.data.cast);
          this.cast=response.data.cast;
        })

    }
    
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
  overflow-y: auto;
  background-color: black;
  opacity: 0;
  transition: linear .2s;

}

.card{
  height: 100%;
  &:hover{ //.card on hover 
    .card-body{
      visibility:visible;
      opacity: 0.8;
      
    }
  }
  .card-body{
      .fa-star{
          color: #ffc107;
        }
  }
  .card-img-top{
    height: 100%;
  }
}
</style>
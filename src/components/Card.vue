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
              <i v-for="index in calcoloVoto(voto)" :key="index" class="fas fa-star"></i>
              <i v-for="index in (5-calcoloVoto(voto))" :key="index" class="far fa-star"></i>
            </div>
            <div>
              {{descrizione}}
            </div>
            <div v-if="cast.length > 0"><h4 class="mt-2">Cast</h4></div>
            <div class="cast" v-for="(p,index) in cast.slice(0 , 5)" :key="index">
              {{p.name}} : 
              {{p.character}}
            </div>
            <!-- <div v-for="(gen,index) in generi" :key="index">
              {{this.gen}}
            </div> -->
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
        genresTv: [],
        genresMovie: [],
        // visualizzaGen:[],
      }
    },
    props:{
      id : Number,  //id del film/serieTV
      generi : Array, //array generi della singola card
      originalLanguage: String, 
      title : String, 
      originalTitle: String,
      descrizione : String,
      voto: Number,
      popularity:Number,
      type: String, //tv / movie
      locandina: String,
      path: String //parte finale del path name per la locandina
    },
    methods:{
      calcoloVoto(voto){
        // console.log("voto :" , voto);
        return Math.round(voto / 2)
      },

      // generiTest(){
      //   console.log("ciao");
      //   console.log(this.genresTv);
      //   this.genresTv.forEach((element,i) =>{
      //        if( (this.type == "tv") && (element == this.generi[i])){
      //         console.log(this.generi[i]);
      //        }
      //   })
     
      // },

       test(){
          // this.cast="";
          let urlCast = "https://api.themoviedb.org/3/"+this.type+"/"+this.id+"/credits?api_key=75ebf4a5bf0762d3887d0146d0d76336"
          console.log(urlCast);
          axios
          .get(urlCast)
          .then(response =>{
            // console.log(response.data.cast);
            this.cast=response.data.cast;
          })
      }
    },
    created(){
      //genres ids array per film e serie tv {id : numero , name :"genereX"}
      // axios
      //   .all([
      //     axios.get("https://api.themoviedb.org/3/genre/movie/list?api_key=75ebf4a5bf0762d3887d0146d0d76336"),
      //     axios.get("https://api.themoviedb.org/3/genre/tv/list?api_key=75ebf4a5bf0762d3887d0146d0d76336"),

      //   ])
      //   .then(axios.spread((genresTvResponse , genresMovieResponse) =>{
      //     this.genresTv = genresTvResponse.data.genres;
      //     this.genresMovie = genresMovieResponse.data.genres;
      //     console.log(this.genresTv);
      //     console.log(this.genresMovie);
      //     // this.generiTest();

      //   }));      
    },
    mounted(){
      // this.test();
         let urlCast = "https://api.themoviedb.org/3/"+this.type+"/"+this.id+"/credits?api_key=75ebf4a5bf0762d3887d0146d0d76336"
          console.log(urlCast);
          axios
            .get(urlCast)
            .then(response =>{
              // console.log(response.data.cast);
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
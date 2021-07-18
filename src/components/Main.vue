<template>
    <!-- per utilizzare lo stesso component ma con due oggetti in cui il nome 
    delle propietà è diverso , devo prima andare a scomporre l'oggetto e passare
    le propietà tramite props e NON l'oggetto per intero  -->

    <!-- push di prova secondo push di prova-->
  <div class="main_wrapper container py-3">
        <div class="row row-cols-3 gy-2">
            <Card v-for="(element,index) in film" :key="index" 
                :id="element.id"
                :generi="element.genres_id" 
                :locandina="'https://image.tmdb.org/t/p/w342'+element.poster_path"
                :path="element.poster_path"
                :title="element.title"
                :originalTitle="element.original_title"
                :descrizione="element.overview"
                :type="'movie'"
                :originalLanguage="element.original_language"
                :voto="element.vote_average"
                :popularity="element.popularity"
            /> 
            <Card v-for="(element2,index2) in series" :key="index2"
                :id="element2.id" 
                :generi="element2.genres_id" 
                :locandina="'https://image.tmdb.org/t/p/w342'+element2.poster_path"
                :path="element2.poster_path"
                :title="element2.name"
                :originalTitle="element2.original_name"
                :descrizione="element2.overview"
                :type="'tv'"
                :originalLanguage="element2.original_language"
                :voto="element2.vote_average"
                :popularity="element2.popularity"
            />
        </div>
  </div>
</template>
<script>

import Card from './Card.vue'
export default {
    name: 'Main',
    components: {
        Card
    },
    props:["film","series"], //le prop in arrivo da app.vue 
    data() {
        return {
            tvGenres : this.series,
            filmIDs : this.film.id,
        }
    },
}
</script>

<style lang="scss" scoped>

</style>
<template>
    <!-- per utilizzare lo stesso component ma con due oggetti in cui il nome 
    delle propietà è diverso , devo prima andare a scomporre l'oggetto e passare
    le propietà tramite props e NON l'oggetto per intero  -->
  <div class="main_wrapper container">
      Main
        <Card v-for="element in film" :key="element.id" 
            :locandina="'https://image.tmdb.org/t/p/w342'+element.backdrop_path"
            :path=element.backdrop_path
            :title="element.title"
            :originalTitle="element.original_title"
            :type="'Film'"
            :originalLanguage="element.original_language"
            :voto="element.vote_average"
            :popularity="element.popularity"
        /> 
        <Card v-for="element2 in series" :key="element2.id" 
            :locandina="'https://image.tmdb.org/t/p/w342'+element2.backdrop_path"
            :path=element2.backdrop_path
            :title="element2.original_name"
            :originalTitle="element2.original_name"
            :type="'Serie'"
            :originalLanguage="element2.original_language"
            :voto="element2.vote_average" 
            :popularity="element2.popularity"
        />
  </div>
</template>
<script>
// https://image.tmdb.org//t/p/w220_and_h330_face/AmHOQ7rpHwiaUMRjKXztnauSJb7.jpg"

import Card from './Card.vue'
export default {
    name: 'Main',
    components: {
        Card
    },
      //      :originalTitle="element.original_title"
    props:["film","series"] //le prop in arrivo da app.vue 
}
</script>

<style lang="scss" scoped>

</style>
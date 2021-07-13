<template>
    <!-- per utilizzare lo stesso component ma con due oggetti in cui il nome 
    delle propietà è diverso , devo prima andare a scomporre l'oggetto e passare
    le propietà tramite props e NON l'oggetto per intero  -->
  <div class="main_wrapper container">
      Main
        <Card v-for="element in film" :key="element.id" 
            :title="element.title"
            :type="'Film'"
            :originalLanguage="element.original_language"
            :voto="element.vote_average"
        /> 
      <!-- <div  v-if="series.length" > -->
        <Card v-for="element2 in series" :key="element2.id" 
          :title="element2.original_name"
          :type="'Serie'"
          :originalLanguage="element2.original_language"
          :voto="element2.vote_average" 
        />
        <!-- </div> -->
  </div>
</template>

<script>
import Card from './Card.vue'
export default {
    name: 'Main',
    components: {
        Card
    },
    props:["film","series"] //le prop in arrivo da app.vue
}
</script>

<style lang="scss" scoped>

</style>
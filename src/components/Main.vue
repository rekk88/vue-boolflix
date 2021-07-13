<template>
  <div class="main_wrapper container">
      Main
      <Card v-for="element in film" :key="element.id" :francesco="element"/>
  </div>
</template>

<script>
import Card from './Card.vue'
export default {
    name: 'Main',
    components: {
        Card
    },
    props:["film"]
}
</script>

<style lang="scss" scoped>

</style>
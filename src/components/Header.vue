<template>
  <div class="header_wrapper container-fluid d-flex justify-content-between align-items-center">
      <div class="logo_wrapper">
          boolflix
      </div>
      <input type="text" placeholder="inserisci un titolo"  v-model="ricerca" class="mx-2" @keyup.enter="$emit('getFilmsEmit',ricerca); $emit('getTvEmit',ricerca)">
  </div>
</template>

<script>
export default {
    name:"Header",
    data() {
        return {
            ricerca:""
        }
    },
}
</script>

<style lang="scss" scoped>
    .header_wrapper{
        height: 70px;
        background-color: #111213;
        .logo_wrapper{
            font-size: 2rem;
            color: #e50914;
            text-transform: uppercase;
        }
        input{
            height: 2rem;
        }

    }
</style>
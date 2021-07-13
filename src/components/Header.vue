<template>
  <div class="header_wrapper container-fluid d-flex justify-content-center align-items-center">
      <input type="text" placeholder="inserisci un titolo"  v-model="ricerca" class="mx-2" @keyup.enter="$emit('getFilmsEmit',ricerca)">
      <button type="button" class="btn btn-secondary" @click="$emit('getFilmsEmit',ricerca)">Cerca</button>
  </div>
</template>

<script>
import {eventBus} from '../main.js'
export default {
    name:"Header",
    components:{

    },
    data() {
        return {
            ricerca:""
        }
    },
    updated(){
            eventBus.$emit('aggiorna',"testo aggiornato");
            console.log("testo aggiornato");
            // return this.ricerca

    },
    methods:{
       
    }
}
</script>

<style lang="scss" scoped>
    .header_wrapper{
        height: 70px;
        background: #2c3e50;
        input{
            height: 2rem;
        }

    }
</style>
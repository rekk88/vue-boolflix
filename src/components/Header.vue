<template>
  <div class="header_wrapper container-fluid">
      <input type="text" placeholder="inserisci un titolo">
  </div>
</template>

<script>
export default {
    name:"Header"
}
</script>

<style lang="scss" scoped>
@import "bootstrap";
    .header_wrapper{
        height: 70px;
        background: #2c3e50;
    }
</style>
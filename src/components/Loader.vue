<template>
  <div class="loader">
    Ładowanie...
  </div>
</template>

<script>
  export default {
    name: 'Loader'
  }
</script>

<style lang="scss" scoped>
  .loader {
    position: absolute;
    left: 0;
    top: 0;
    width: 100vw;
    height: 100vh;
    background: rgba(black, 0.5);
    display: flex;
    justify-content: center;
    align-items: center;
    z-index: 2;
  }
</style>

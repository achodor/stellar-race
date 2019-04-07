<template>
  <div id="app">
    <h1>🚀 Gwiezdny wyścig ✨</h1>
    <AddForm/>
  </div>
</template>

<script>
  import AddForm from '@/components/AddForm.vue';

  export default {
    name: 'app',
    components: {
      AddForm
    }
  }
</script>

<style lang="scss">
  @import url('https://fonts.googleapis.com/css?family=Poppins:600,700');
  @import '@/scss/_colors.scss';

  * {
    box-sizing: border-box;  
    font-family: 'Poppins', sans-serif;
  }

  body { 
    background: #333;
    color: white;
  }

  #app {
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    padding: 10px 0 0;
    margin: 0 auto;

    h1 {
      text-align: center;
    }
  }
</style>

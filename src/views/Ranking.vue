<template>
  <div class="ranking">
    <Repo
      color='#ff00ff'
      :place='1'
      name='vuejs/vue'
      :stars='123456'
    />
    <Repo
      color='#ff0000'
      :place='2'
      name='facebook/react'
      :stars='21412'
    />
  </div>
</template>

<script>
  import Repo from '@/components/Repo.vue';

  export default {
    name: 'ranking',
    components: {
      Repo
    }
  }
</script>

<style lang="scss" scoped>
  .ranking {
    width: 800px;
    margin: 0 auto;
  }
</style>

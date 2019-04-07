<template>
  <div class="ranking">
    <Repo
      color='#4BBD8A'
      :place='1'
      name='vuejs/vue'
      :stars='123456'
    />
    <Repo
      color='#61DAFB'
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
    width: calc(100% - 22px);
    margin: 0;
    padding: 0 16px 140px;

    @media (min-width: 860px) {
      width: 800px;
      margin: 0 auto;
    }
  }
</style>
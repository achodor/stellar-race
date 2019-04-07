<template>
  <div class="ranking">
    <Repo/>
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

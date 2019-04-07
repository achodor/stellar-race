<template>
  <div class="ranking">
    <Repo v-for="(repo, index) in repos" :key="repo.stars"
      :color=repo.color
      :place=index+1
      :name=repo.name
      :stars=repo.stars
    />
  </div>
</template>

<script>
  import Repo from '@/components/Repo.vue';

  export default {
    name: 'ranking',
    components: {
      Repo
    },
    data() {
      return {
        repos: [
          {
            name: 'vuejs/vue',
            stars: 123456,
            color: '#42b983'
          }, 
          {
            name: 'facebook/react',
            stars: 21412,
            color: '#61DAFB'
          }
        ]
      }
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
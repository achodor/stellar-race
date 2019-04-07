<template>
  <div id="app">
    <h1>🚀 Gwiezdny wyścig ✨</h1>
    <div class="ranking">
      <Repo v-for="(repo, index) in repos" :key="repo.name"
        :color=repo.color
        :place=index+1
        :name=repo.name
        :stars=repo.stars
        @deleteRepo="deleteRepo(index)"
      />
    </div>
    <AddForm @sendData="getData"/>
  </div>
</template>

<script>
  import AddForm from '@/components/AddForm.vue';
  import Repo from '@/components/Repo.vue';
  import axios from 'axios';

  export default {
    name: 'app',
    components: {
      AddForm,
      Repo
    },
    data() {
      return {
        repos: []
      }
    },
    methods: {
      async getData(repo) {
        await axios.get('https://api.github.com/repos/' + repo.name)
          .then(function (response) {
            repo.stars = response.data.stargazers_count
          })
          .catch(function (error) {
            console.log(error)
          });

        this.repos.push(repo)
        this.sortRepos()
      },
      deleteRepo(index) {
        this.repos.splice(index, 1);
        this.sortRepos();
      },
      sortRepos() {
        return this.repos.sort((a, b) => a.stars - b.stars).reverse();
      }
    },
    mounted() {
      this.sortRepos()
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
    margin: 0 auto;
  }

  #app {
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    padding: 10px 0 0;
    margin: 0 auto;

    h1 {
      text-align: center;
      font-size: 1.5em;

      @media (min-width: 860px) {
        font-size: 2em;
      }
    }

    .ranking {
      width: calc(100% - 22px);
      margin: 0;
      padding: 0 16px 160px;

      @media (min-width: 860px) {
        width: 800px;
        margin: 0 auto;
      }
    }
  }
</style>
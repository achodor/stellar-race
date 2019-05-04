<template>
  <div id="app">
    <Loader v-if="pending">
      <template #text>Ładowanie...</template>
    </Loader>
    <h1>🚀 Gwiezdny wyścig ✨</h1>
    <div class="ranking">
      <Repo v-for="(repo, index) in repos" :key="repo.name + '-' + index"
        :color=repo.color
        :place=index+1
        :name=repo.name
        :stars=repo.stars
        @deleteRepo="deleteRepo(index)"
      />
    </div>
    <transition name="error">
      <div class="error" v-show="error">
        Próba pobrania danych z API GitHub nie powiodła się! 😢
        <button class="error-close" @click="error = false"><img src="@/assets/times.svg" alt="x"></button>
      </div>
    </transition>
    <AddForm @sendData="getData"/>
  </div>
</template>

<script>
  import AddForm from '@/components/AddForm.vue';
  import Loader from '@/components/Loader.vue';
  import Repo from '@/components/Repo.vue';
  import axios from 'axios';

  export default {
    name: 'app',
    components: {
      AddForm,
      Repo,
      Loader
    },
    data() {
      return {
        repos: [],
        error: false,
        pending: false
      }
    },
    methods: {
      async getData(repo) {
        this.error = false;
        this.pending = true;
        await axios.get('https://api.github.com/repos/' + repo.name)
          .then(function (response) {
            repo.stars = response.data.stargazers_count;
          })
          .catch(() => {
            this.error = true;
          })
          .then(() => {
            this.pending = false;
          });

        if(!this.error) {
          this.repos.push(repo)
          this.sortRepos();
        }
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
      this.sortRepos();
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
    background: $dark;
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

    .list-enter-active, .list-leave-active {
      transition: all 1s;
    }

    .list-enter, .list-leave-to {
      opacity: 0;
      transform: translateY(30px);
    }

    .error {
      position: fixed;
      bottom: 184px;
      left: 0;
      width: 100%;
      text-align: center;
      background: $danger;
      padding: 12px 0;
      font-size: .75em;

      @media (min-width: 860px) {
        bottom: 140px;
      }

      .error-close {
        background: none;
        border: none;
        cursor: pointer;
        padding: 0;
        outline: none;
        position: absolute;
        right: 20px;
        bottom: calc(50% - 10px);
        opacity: .7;

        img { 
          width: 8px;
          height: 8px;
        }
      }
    }

    .error-enter-active, .error-leave-active {
      opacity: 0;
      transform: translateY(30px);
      transition: all 1s;
    }
  }
</style>
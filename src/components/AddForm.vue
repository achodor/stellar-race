<template>
    <div class="add-form">
      <div class="wrapper">
        <h2>Dodaj repozytorium:</h2>
        <div class="btn-group">
          <div class="color-preview" :style="{ background: repo.color }"></div>
          <input class="color-input" type="text" v-model="repo.color" :style="{ color: repo.color }">
          <button class="add-btn" @click="sendData">Dodaj</button>
        </div>
        <input
          class="repo-input"
          type="text"
          placeholder="właściciel/nazwa repozytoruim"
          v-model="repo.name"
          v-on:keyup.enter="sendData">
      </div>
    </div>
</template>

<script>
  export default {
    name: 'addForm',
    data() {
      return {
        repo: {
          color: '#42b883',
          name: ''
        }
      }
    },
    methods: {
      sendData() {
        const newRepo = Object.assign({}, this.repo);  
        this.$emit('sendData', newRepo);
      }
    }
  }
</script>

<style lang="scss" scoped>
  @import '@/scss/_colors.scss';

  .add-form {
    position: fixed;
    width: 100%;
    height: 140px;
    background: white;
    bottom: 0;

    .wrapper {
      width: calc(100% - 22px);
      margin: 0 auto;
      display: grid;
      grid-template-columns: 1fr 1fr;
      grid-template-areas: "header buttons"
                            "input input";
      padding: 25px 16px 0;

      @media (min-width: 860px) {
        width: 800px;
      }

      h2 {
        color: $dark;
        grid-area: header;
        margin: 0 0 20px;
        font-size: 1em;

        @media (min-width: 860px) {
            font-size: 1.5em;
        }
      }

      .btn-group {
        grid-area: buttons;
        text-align: right;

        .color-preview {
          background: $dark;
          width: 16px;
          height: 16px;
          border-radius: 2px;
          display: inline-block;
          margin-right: 10px;
          vertical-align: middle;
        }

        .color-input {
          color: $dark;
          width: 70px;
          border: none;
          background: transparent;
          outline: none;
        }

        .add-btn {
          background: darken($dark, 5%);
          color: white;
          border: none;
          outline: none;
          cursor: pointer;
          position: absolute;
          bottom: 140px;
          width: 100%;
          transition: all .25s;
          left: 0;
          padding: 12px 0;

          &:hover {
            background: darken($dark, 10%);
          }

          @media (min-width: 860px) {
            border-radius: 6px;
            padding: 6px 20px;
            margin-left: 20px;
            position: static;
            width: auto;
            background: $dark;

            &:hover {
              background: darken($dark, 5%);
            }
          }
        }
      }

      .repo-input {
        grid-area: input;
        border: none;
        border-bottom: 2px solid $border;
        padding: 5px 0;
        background: transparent;
        outline: none;
        color: $dark;
        font-size: 16px;

        &::placeholder {
          color: $light;
        }
      }
    }
  }
</style>
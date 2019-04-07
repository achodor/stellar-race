<template>
    <div class="add-form">
      <div class="wrapper">
        <h2>Dodaj repozytorium:</h2>
        <div class="btn-group">
          <div class="color-preview" :style="{ background: color }"></div>
          <input class="color-input" type="text" v-model="color" :style="{ color: color }">
          <button class="add-btn">Dodaj</button>
        </div>
        <input class="repo-input" type="text" placeholder="właściciel/nazwa repozytoruim">
      </div>
    </div>
</template>

<script>
  export default {
    name: 'addForm',
    data() {
      return {
        color: '#22d8c2'
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
      width: 800px;
      margin: 0 auto;
      display: grid;
      grid-template-columns: 1fr 1fr;
      grid-template-areas: "header buttons"
                            "input input";
      padding: 25px 0 0 0;

      h2 {
        color: $dark;
        grid-area: header;
        margin: 0 0 20px;
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
          background: $dark;
          color: white;
          border: none;
          outline: none;
          cursor: pointer;
          border-radius: 6px;
          padding: 6px 20px;
          transition: all .25s;
          margin-left: 20px;

          &:hover {
            background: darken($dark, 5%);
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
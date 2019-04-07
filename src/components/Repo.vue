<template>
  <div class="repo">
    <div class="repo-wrapper" :style="{ background: color }">
      <span class="name">{{ place }}. {{ name }}</span>
      <span class="stars">{{ stars }}</span>
    </div>
    <img class="stars-svg" src="@/assets/stars.svg" alt="*" v-show="place === 1">
    <button class="repo-delete" @click="deleteRepo(place-1)"><img src="@/assets/times.svg" alt="x"></button>
  </div>
</template>

<script>
  export default {
    name: 'repo',
    props: {
      color: {
        type: String,
        required: true
      },
      place: {
        type: Number,
        required: true
      },
      name: {
        type: String,
        required: true
      },
      stars: {
        type: Number,
        required: true
      }
    },
    methods: {
      deleteRepo(index) {
        this.$emit('deleteRepo', index);
      }
    }
  }
</script>

<style lang="scss" scoped>
  .repo {
    width: 100%;
    position: relative;
    margin-bottom: 20px;

    &:last-of-type {
      margin: 0;
    }

    .repo-wrapper {
      width: 100%;
      padding: 10px 20px;
      background: blue;
      color: white;
      display: flex;
      justify-content: space-between;
      border-radius: 6px;
    }

    .stars-svg {
      position: absolute;
      right: -15px;
      top: -20px;
    }

    .repo-delete {
      position: absolute;
      left: calc(100% + 10px);
      top: calc(50% - 10px);
      background: none;
      border: none;
      cursor: pointer;
      padding: 0;
      outline: none;
    }
  }
</style>
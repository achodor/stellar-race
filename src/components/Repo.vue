<template>
  <div class="repo">
    <div class="repo-wrapper">
      <span class="name">1. vuejs/vue</span>
      <span class="stars">134651</span>
    </div>
    <img class="stars-svg" src="@/assets/stars.svg" alt="*">
    <button class="repo-delete"><img src="@/assets/times.svg" alt="x"></button>
  </div>
</template>

<script>
  export default {
    name: 'repo'
  }
</script>

<style lang="scss" scoped>
  .repo {
    width: 100%;
    position: relative;

    .repo-wrapper {
      width: 100%;
      padding: 10px 20px;
      background: #4BBD8A;
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


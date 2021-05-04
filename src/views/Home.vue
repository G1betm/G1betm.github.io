<template>
  <div class="">
    <div class="home section">
      <div class="home-title" style="opacity: 1" :style="{opacity: 1 - scrollValue*0.002}">
        Our mission is to create virtual worlds <br>
        more meaningful than real life
      </div>
    </div>
    <div class="home-info section">

    </div>
  </div>
</template>

<script>
  // @ is an alias to /src
  export default {
    name: 'Home',
    components: {

    },
    data() {
      return {
        scrollValue: null
      }
    },
    created() {
      window.addEventListener('scroll', this.handleScroll);
    },
    destroyed() {
      window.removeEventListener('scroll', this.handleScroll);
    },
    methods: {
      handleScroll() {
        this.scrollValue = window.scrollY;
      }
    },
  }
</script>

<style lang="scss">
  .home {
    background-image: url('../assets/img/header-bg.jpg');
    display: flex;
    align-items: center;
    justify-content: center;
    color: #fff;
    &-title {
      font-size: 50px;
      text-align: center;
    }
    &-info {
      background-image: url('../assets/img/games-bg.webp');
    }
  }
</style>
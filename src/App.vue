<template>
  <div id="app">
    <header class="header">
      <div class="container">
        <div class="header-content" :class="{pinned: scrollValue > 50}">
          <a href="#" class="header-logo">
            G1BE
          </a>
          <div class="nav">
            <router-link class="nav-item" to="/">Home</router-link>
            <router-link class="nav-item" to="/about">About</router-link>
            <router-link class="nav-item" to="/games">Games</router-link>
          </div>
        </div>
      </div>
    </header>
    <router-view />
    
  </div>
</template>

<script>
  export default {
    data() {
      return {
        scrollValue: null,
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
  /* width */
  ::-webkit-scrollbar {
    width: 0px;
  }

  html {
    overflow-x: hidden;
    scroll-behavior: smooth;
  }

  body {
    min-height: 100vh;
    margin: 0;
    font-family: 'Russo One', sans-serif;
    background: #212121;
  }

  a {
    text-decoration: none;
    color: inherit;
  }

  * {
    box-sizing: border-box;
  }

  .header {
    background: #212121;
    color: #fff;
    position: fixed;
    top: 0;
    width: 100%;
    z-index: 10;
    transition: .3s ease;

    &-content {
      display: flex;
      justify-content: space-between;
      align-items: center;
      padding: 30px 0;
      transition: .3s ease;
    }

    &-logo {
      font-size: 22px;
    }
  }

  .pinned {
    padding: 15px 0;
    background-color: transparent;
  }

  .container {
    max-width: 1550px;
    margin: 0 auto;
  }

  .link-hover {
    position: relative;

    &::before {
      content: '';
      width: 0;
      height: 1px;
      position: absolute;
      bottom: 0;
      left: 0;
      background: #fff;
      transition: width .2s ease-in;
    }

    &:hover {
      &::before {
        width: 100%;
      }
    }
  }

  .nav {
    a {
      display: inline-block;
    }

    &-item {
      margin: 15px;
      font-size: 18px;
      position: relative;

      &::before {
        content: '';
        width: 0;
        height: 1px;
        position: absolute;
        bottom: 0;
        left: 0;
        background: #fff;
        transition: width .2s ease-in;
      }

      &:hover {
        &::before {
          width: 100%;
        }
      }
    }
  }

  .nav-item.router-link-exact-active::before {
    width: 100%;
  }

  .section {
    min-height: 100vh;
    background-size: cover;
    position: sticky;
    background-repeat: no-repeat;
    background-size: cover;
    background-attachment: fixed;
    top: 0;
  }
</style>
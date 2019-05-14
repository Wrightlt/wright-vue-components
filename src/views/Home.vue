<template>
  <div class="home">
    <div id="nav">
      <router-link to="/">Home</router-link>
      |
      <router-link to="/about">About</router-link>
      |
      <router-link to="/usage">Usage</router-link>
    </div>

    <img alt="Vue logo" src="../assets/home/avatar.jpeg" class="avatar">
    <HelloWorld msg="Welcome to Wright's Vue Common Component Libraries"/>
  </div>
</template>

<script>
  // @ is an alias to /src
  import HelloWorld from '@/components/Hello.vue'

  export default {
    name: 'HomeView',
    components: {
      HelloWorld
    }
  }
</script>

<style lang="scss" scoped>
  .home {
    padding-top: 30px;
  }

  #nav {
    padding: 30px;
    a {
      font-weight: bold;
      color: #2c3e50;
      &.router-link-exact-active {
        color: #42b983;
      }
    }
  }

  .avatar {
    width: 200px;
  }
</style>

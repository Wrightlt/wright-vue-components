<template>
  <div class="home">
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

  .avatar {
    width: 200px;
  }
</style>

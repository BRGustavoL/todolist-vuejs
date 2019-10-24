<template>
  <div id="app">
    <Home></Home>
  </div>
</template>

<script>
import Home from '@/pages/Home/Home.vue';
export default {
  name: 'app',
  components: {
    Home,
  }
}
</script>

<style>
@import url('https://fonts.googleapis.com/css?family=Roboto&display=swap');
#app {
  font-family: 'Roboto', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
</style>

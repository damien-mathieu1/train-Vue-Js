<template>
  <div class="app">
    <HomePage/>
  </div>
</template>

<script>
import HomePage from "./page/HomePage.vue"
export default {
  name: 'App',
  components:{
    HomePage,
  }
}
</script>

<style>
@import url('./style/normalize.css');
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;700&display=swap');
#app {
  font-family: 'Roboto', sans-serif;
  padding: 20px;
}
</style>

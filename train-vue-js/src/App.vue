<template>
  <div class="app">
    <RestaurantCard/>
  </div>
</template>

<script>
import RestaurantCard from './components/RestaurantCard.vue'

export default {
  name: 'App',
  components: { RestaurantCard },


}
</script>

<style>
@import url('./style/normalize.css');
@import url('https://fonts.googleapis.com/css2?family=Roboto:wght@300;400;700&display=swap');
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

<template>
  <div class="app">
    <RestaurantCard/>
    <RestaurantCard/>

    <RestaurantCard/>

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
  font-family: 'Roboto', sans-serif;
}
</style>

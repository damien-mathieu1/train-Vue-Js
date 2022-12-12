<template>
  <p>{{ $route.params.resto }}</p>
</template>

<script>
import BDD from '../BDD'
import { onMounted } from '@vue/runtime-core'
export default {
    name: "RestaurantPage",
    setup(){
      onMounted(()=> {
        console.log(BDD);
      });
    }
}
</script>

<style>

</style>
<template>
  <div class="home">
    <RestaurantRow v-for="(data,index) in data_restaurant" :key="index" :three_restaurant="data"/>
  </div>
</template> 

<script>
//IMPORT
import BDD from "../BDD.js"
import { onMounted, ref } from "vue"

//COMPONENTS
import RestaurantRow from '../components/RestaurantRow.vue'

export default {
    name:"HomePage",
    components: { RestaurantRow },
    setup(){
      class Restaurant{
        constructor(name,note,image,drive_time){
          this.name = name
          this.note = note
          this.image = image
          this.drive_time = drive_time
        }
      }
      let data_restaurant = ref([])
      const makeDataRestaurant = () =>{
        let three_restaurant =[];
        for(const resto of BDD){
          if(three_restaurant.length==2){
            three_restaurant.push(new Restaurant(resto.name,resto.note,resto.image,resto.drive_time));
            data_restaurant.value.push(three_restaurant);
            three_restaurant = [];
          }else{
            three_restaurant.push(new Restaurant(resto.name,resto.note,resto.image,resto.drive_time));
          }
        }
      }
      onMounted(makeDataRestaurant);
      return {
        data_restaurant,
      }
    }
}
</script>

<style>

</style>
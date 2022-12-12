<template>
  <div class="restaurant--row">
    <h2 class="title">
      Nos restaurants  
    </h2>
    <div class="wrapper--card">
        <RouterLink v-for="(card,index) in three_restaurant" :info_restaurant="card" :key="index" :to="{ name : 'Restaurant', params: { resto: card.name}}">
            <restaurant-card :info_restaurant="card"/>
        </RouterLink>
    </div>
   </div>
</template>

<script>
import { RouterLink } from "vue-router";
import RestaurantCard from "./RestaurantCard.vue"
export default {
    name : "RestaurantRow",
    components  :{
    RestaurantCard,
    RouterLink
},
    props:{
        three_restaurant : Array,
    }
}
</script>

<style lang="scss">
.restaurant--row{
    .wrapper--card{
        display: flex;
        align-items: center;
        justify-content: space-between;
    }
}
</style>
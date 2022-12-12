<template>
  <RouterLink to="/">
    <div id="retour">Retour à la page d'accueil</div>

  </RouterLink>
  <img :src="restaurant.image" alt="">
  <p>{{ restaurant.name }}</p>
  <p>Note du restaurant : {{restaurant.note}}</p>
  <p>Temps de livraison : {{restaurant.drive_time}}</p>
</template>

<script>
import BDD from '../BDD'
import { useRoute } from 'vue-router'
export default {
    name: "RestaurantPage",
    setup(){
      const route = useRoute();
      const restaurant = BDD.find((resto)=>{
        if(resto.name == route.params.resto){
            return resto;
          }
      });
      
      return {
        restaurant,
      }
      
    }
}
</script>

<style scoped lang="scss">
  #retour{
    margin: 25px 45px;
    font-weight: 400;
    cursor : pointer;
    
    &:hover {
      font-weight: 900;
    }
  }
</style>>


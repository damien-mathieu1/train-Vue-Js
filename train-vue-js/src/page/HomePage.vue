<template>
  <div class="home">
    <div class="header">
      <img src="https://d3i4yxtzktqr9n.cloudfront.net/web-eats-v2/ee037401cb5d31b23cf780808ee4ec1f.svg" alt="">
      <div class="wrapper--input">
        <input v-model="recherche_resto_util" type="text" name="" id="" placeholder="De quoi avez vous envie ?">
        <div class="search">
          <div v-for="(resto,index) in search_resto" :key="index" class="container--restaurant--search">
            <div class="wrapper--img">
              <img :src="resto.image" alt="" srcset="">
            </div>
            <p>{{resto.name}}</p>
          </div>
        </div>
      </div>
    </div>
    <div class="banner">

    </div>
    <RestaurantRow v-for="(data,index) in data_restaurant" :key="index" :three_restaurant="data" />
  </div>
</template>

<script>
  //IMPORT
  import BDD from "../BDD.js"
  import {
    onMounted,
    ref,
    watch
  } from "vue"

  //COMPONENTS
  import RestaurantRow from '../components/RestaurantRow.vue'

  export default {
    name: "HomePage",
    components: {
      RestaurantRow
    },
    setup() {
      class Restaurant {
        constructor(name, note, image, drive_time) {
          this.name = name
          this.note = note
          this.image = image
          this.drive_time = drive_time
        }
      }
      let data_restaurant = ref([])
      let tous_les_resto = [];
      const makeDataRestaurant = () => {
        let three_restaurant = [];
        for (const resto of BDD) {
          const newResto = new Restaurant(resto.name, resto.note, resto.image, resto.drive_time);
          tous_les_resto.push(newResto);
          if (three_restaurant.length == 2) {
            three_restaurant.push(newResto);
            data_restaurant.value.push(three_restaurant);
            three_restaurant = [];
          } else {
            three_restaurant.push(newResto);
          }
        }
      }
      //Auto complete restaurant search
      let recherche_resto_util = ref("");
      let search_resto = ref([]);
      watch(recherche_resto_util, (new_value) => {
        let regex = RegExp(new_value, 'i');
        let filtre = tous_les_resto.filter(resto => regex.test(resto.name));
        if(new_value == 0){
          search_resto.value =[];
        }
        else{
          search_resto.value =filtre;
        }
      })

      onMounted(makeDataRestaurant);
      return {
        data_restaurant,
        recherche_resto_util,
        search_resto,
      }
    }
  }
</script>

<style lang="scss">
  .home {
    .header {
      height: 120px;
      width: 100%;
      display: flex;
      align-items: center;
      justify-content: space-between;

      img {
        width: 300px;
      }

      .wrapper--input {
        position: relative;

        input {
          background-color: #f6f6f6;
          border: none;
          height: 60px;
          width: 400px;
          outline: none;
          padding: 0px 20px;
        }

        .search {
          position: absolute;
          top: 100%;
          width: 100%;
          background-color: #ffff;

          .container--restaurant--search{
            display: flex;
            align-items: center;
            .wrapper--img{
              height: 40px;
              width: 40px;
              margin-right: 25px;
              border-radius: 50%;
              overflow: hidden;
              img{
                height: 100%;
                width: auto;
              }
            }
          }
        }
      }

    }

    .banner {
      height: 300px;
      width: 100%;
      background-image: url("https://ubernewsroomapi.10upcdn.com/wp-content/uploads/sites/345/2016/03/blog_960x540-960x540.jpg");
      background-size: auto;
      background-position: center center;
    }
  }
</style>
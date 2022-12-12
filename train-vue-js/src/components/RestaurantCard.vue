<template>
    <div class="restaurant--card">
        <div :style="changeBackground"  class="restaurant--image">

        </div>
        <div class="restaurant--informations">
            <div class="top">
                <p class="name">{{info_restaurant.name}}</p>
                <p class="note"><span>{{info_restaurant.note}}</span></p>
            </div>
            <p class="time">{{info_restaurant.drive_time}}</p>
        </div>
    </div>
</template>

<script>
//IMPORT
import { computed } from 'vue';
export default {
    name : "RestaurantCard",
    props:{
        info_restaurant : Object,
    },
    setup(props){
        const changeBackground = computed(() =>{
            return {
                backgroundImage: `url(${props.info_restaurant.image})`
            }
        })


        return {
            changeBackground
        }
    }
    
}
</script>

<style lang="scss">
.restaurant--card{
    width: 100%;
    height: 30vh;
    p{      
        margin: 0px;
    }
    .restaurant--image{
        height: 70%;
        background-size: cover;
        background-position : center;
    }
}

.restaurant--informations{
    .top{
        margin: 10px 0px;
        display: flex;
        justify-content: space-between;
        align-items: center;
        .note{
            display: flex;
            align-items: center;
            justify-content: center;
            background-color: #eeee;
            padding: 5px;
            border-radius: 50%;
            font-size: 0.8rem;
        }
    }
    .time{
        font-size: 0.9rem;
    }
}

</style>
<script>
import {store} from '../store.js';

export default{
    data() {
        return{
            store,
        }
    },
    props:{
        arraycard:{
            type: Object,
            required: true,
        }
    },
    
}
</script>

<template>
    <div class="card my_dimension_card" >
            <img :src="arraycard.card_images[0].image_url" class="card-img-top" :alt="arraycard.name">
        <div class="card-body">
            <p class="card_text">{{ arraycard.name }}.</p>
            <p class="card_text my_typecard">{{ arraycard.archetype }}.</p>
        </div>
        </div>
</template>

<style scoped>
    .my_dimension_card{
    height: 100%;
}
    .card-body{
        background-color: #d48f38;
        text-align: center;
        padding-left: 0;
        padding-right: 0;

            p:first-child{
                color: white;
                font-weight: bold;
        }
    }

</style>
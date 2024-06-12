<script>
import MainListSingleCard from './MainListSingleCard.vue';
import {store} from '../store.js';

export default{
    data() {
        return{
            store,
        }
    }
}
</script>

<template>
    <div v-for="(card, index) in store.cards.data" class="my_margin" :key="index">
        <div class="card" style="width: 12rem">
            <img :src="card.card_images[0].image_url" class="card-img-top" :alt="card.name">
        <div class="card-body">
            <p class="card-text">{{ card.name }}.</p>
        </div>
        </div>
    </div> 
</template>

<style lang="scss" scoped>
    

</style>
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
    <div v-for="(card, index) in store.cards.data" :key="index" class="my_cards p-3">
        <div class="card" >
            <img :src="card.card_images[0].image_url" class="card-img-top" :alt="card.name">
        <div class="card-body">
            <p class="card-text">{{ card.name }}.</p>
        </div>
        </div>
    </div> 
</template>

<style lang="scss" scoped>
    .my_cards{
        margin: 0 auto;
    width: calc(100% / 5);
}

</style>
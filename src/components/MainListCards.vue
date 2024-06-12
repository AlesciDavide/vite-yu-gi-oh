<script>
import MainListSingleCard from './MainListSingleCard.vue';
import {store} from '../store.js';

export default{
    data() {
        return{
            store,
        }
    },
    components:{
        MainListSingleCard,
    }
}
</script>

<template>
    
    <div v-for="(card, index) in store.cards.data" :key="index" class="my_cards p-3">
        <MainListSingleCard :arraycard="card" />
        
    </div> 
</template>

<style lang="scss" scoped>
    .my_cards{
        margin: 0 auto;
        width: calc(100% / 5);
}
</style>
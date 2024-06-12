<script>
import MainListCards from './MainListCards.vue'
import MainListSingleCard from './MainListSingleCard.vue'
import axios from 'axios';
import {store} from '../store.js';

export default{
    components:{
        MainListCards,
        
    },
    data() {
        return{
            store,
        }
    },
    methods:{
        getCards(){
            axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0').then(response => {
                this.store.cards = response.data;
                console.log(store.cards.data);
            })
            .catch(function (error) {
                // handle error
                console.log(error);
            })
            .finally(function () {
                // always executed
            });
        }
    },
    created(){
        this.getCards();
    }
}
</script>

<template>
    <main >
        <section class="my_container d-flex">
            <div class="my_container_cards d-flex">
                <MainListCards />
            </div>
        </section>
    </main>
</template>

<style lang="scss" scoped>
main{
    background-color: #d48f38;
    padding-top: 3rem;
}

.my_container{
    width: 80%;
    margin: 0 auto;
    background-color: white;
}

.my_container_cards{
    flex-wrap: wrap;
    margin: 0 auto;
}


</style>
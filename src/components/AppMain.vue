<script>
import MainListCards from './MainListCards.vue'
import AppLoader from './AppLoader.vue'
import MainSearch from './MainSearch.vue'
import axios from 'axios';
import {store} from '../store.js';

export default{
    components:{
        MainListCards,
        AppLoader,
        MainSearch,
    },
    data() {
        return{
            store,
            isLoader: false, 
        }
    },
    methods:{
        
        
        getCards(){
            
            axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?archetype=' + store.archetypeSelected).then(response => {
                this.isLoader = false;
                setTimeout(() => {
                    this.isLoader = true;
                }, 300);
        
                this.store.cards = response.data;
                console.log(response.data);
                
            })
            .catch(function (error) {
                // handle error
                console.log(error);
            })
            .finally(function () {
                // always executed
            });
        },
        
        
    },
    created(){
        this.getCards();
        
        
    },
}
</script>

<template>
    <main >
        
        <div class="full_container" v-if="isLoader == true">
            <MainSearch @changecard="getCards()"/>
            <section  class="my_container">
                <h3>
                    Found {{store.cards.data.length}} cards
                </h3>
                
                <div class="my_container_cards d-flex">
                    <MainListCards />
                </div>
            </section>
            
            </div>
                <div class="myLoader" v-else="!isLoader">
                    <AppLoader/>
                </div>
    </main>
</template>

<style lang="scss" scoped>
.full_container{
    background-color: #d48f38;
    padding: 3rem 0;
}

.my_container{
    width: 80%;
    margin: 0 auto;
    background-color: white;
    padding: 1rem 0;
    

    h3{
            background-color: black;
            color: white;
            padding: .5rem 0;
            margin-bottom: 0;
        }
}

.my_container_cards{
    flex-wrap: wrap;
    margin: 0 auto;
    overflow-y: scroll;

        
}

.myLoader{
    display: flex;
    justify-content: center;
    align-self: center;
    height: 100%;
    margin-top: 40vh;
}

</style>
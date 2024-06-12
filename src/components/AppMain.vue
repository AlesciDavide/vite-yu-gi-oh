<script>
import MainListCards from './MainListCards.vue'
import AppLoader from './AppLoader.vue'
import axios from 'axios';
import {store} from '../store.js';

export default{
    components:{
        MainListCards,
        AppLoader,
    },
    data() {
        return{
            store,
            isLoader: false,
        }
    },
    methods:{
        getCards(){
            axios.get('https://db.ygoprodeck.com/api/v7/cardinfo.php?num=20&offset=0').then(response => {
                this.store.cards = response.data;
                console.log(store.cards.data);
                this.isLoader = true;
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
        console.log(store.length);
    }
}
</script>

<template>
    <main >
        <div class="full_container" v-if="isLoader == true">
            <section  class="my_container">
                <h3>
                    Found {{store.cards.data.length }} cards
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
    padding-top: 3rem;
}

.my_container{
    width: 80%;
    margin: 0 auto;
    background-color: white;

    h3{
            background-color: black;
            color: white;
            padding: .5rem 0;
        }
}

.my_container_cards{
    flex-wrap: wrap;
    margin: 0 auto;

        
}

.myLoader{
    display: flex;
    justify-content: center;
    align-self: center;
    height: 100%;
    margin-top: 40vh;
}

</style>
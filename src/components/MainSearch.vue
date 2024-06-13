<script>
import {store} from '../store.js';
import axios from 'axios';

export default{
    data() {
        return{
            store,
        }
    },
    methods:{
        findarchetype(){
                axios.get('https://db.ygoprodeck.com/api/v7/archetypes.php').then(response => {
                    this.store.archetype = response.data;
                    console.log(store.archetype[0].archetype_name);
                    console.log(store.archetype);
                    
                })
                .catch(function (error) {
                    // handle error
                    console.log(error);
                })
                .finally(function () {
                    // always executed
                });
            },
            changed(archetype){
                store.archetypeSelected = archetype;
            }

    },
    created(){
        this.findarchetype();
        
        
    },
}
</script>

<template>


    <select name="archetype" id="archetype">
        <option v-for="(archetype) in store.archetype" :value="archetype.archetype_name" @click="changed(archetype.archetype_name), $emit('changecard')">{{ archetype.archetype_name }}</option>
    </select>


</template>

<style lang="scss" scoped>
    
</style>
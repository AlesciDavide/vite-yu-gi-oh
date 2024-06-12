<script>
import AppMain from './components/AppMain.vue'
import AppHeader from './components/AppHeader.vue'

export default {
    components:{
        AppMain,
        AppHeader,
    }
}

</script>

<template>
    <AppHeader/>
    <AppMain/>
</template>

<style lang="scss">
@use './styles/general.scss';
@use '../node_modules/bootstrap/scss/bootstrap.scss' as *;


</style>

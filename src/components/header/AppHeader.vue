<template>
  <header >
    <HeaderAdvertise/>
    <img src="../../assets/img/avada-food-logo.png" class="my-3" alt="">
    <AppNav :admin="admin"/>
    <AppJambo :admin="admin"/>
  </header>
</template>

<script>
import HeaderAdvertise from './HeaderAdvertise.vue';
import AppNav from './AppNav.vue';
import AppJambo from './AppJambo.vue';
export default {
    components: { HeaderAdvertise, AppNav, AppJambo },
    props:{
      admin: Boolean
    }
}
</script>

<style lang="scss" scoped>
@import "../../assets/style/header";
</style>
<template>
  <div id="app">
   <AppHeader/>
   <AppMain />
   <AppFooter />
  </div>
</template>

<script>
import AppHeader from './components/header/AppHeader.vue';
import AppMain from './components/main/AppMain.vue';
import AppFooter from './components/footer/AppFooter.vue';

export default {
  name: 'App',
  components: {
    AppHeader,
    AppMain,
    AppFooter
}
}
</script>

<style lang="scss">
@import "./assets/style/global";
h1{
  font-family: $font-cat;
}
</style>

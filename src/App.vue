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
@import url('https://fonts.googleapis.com/css2?family=Vidaloka&display=swap');
h1{
 font-family: 'Vidaloka', serif;
}
.link{
  color: $org-color;
  background-color: white;
  width: 50px;
  height: 50px;
  font-size: 20px;
  display: flex;
  align-items: center;
  justify-content: center;
  border-radius: 50%;
}
html{
  background-color: white;
}
</style>

<template>
  <main class="container">
    <AppJournal :admin="admin" />
    <MainSectionPopular :admin="admin"/>
    <MainSectionCollection :admin="admin"/>
    <MainSectionNews :admin="admin"/>
</main>
</template>

<script>
import MainSectionPopular from './MainSectionPopular.vue';
import AppJournal from './AppJournal.vue';
import MainSectionCollection from './MainSectionCollection.vue'; MainSectionCollection
import MainSectionNews from './MainSectionNews.vue'; 
export default {
    components: { MainSectionPopular, AppJournal, MainSectionCollection, MainSectionNews },
    props:{
      admin : Boolean
    }
}
</script>

<style lang="scss" scoped>
main{
}
</style>
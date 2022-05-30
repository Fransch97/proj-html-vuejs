<template>
  <main class="container">
  <AppJournal />
    <MainSectionPopular />
    <MainSectionCollection />
    <MainSectionNews />
</main>
</template>

<script>
import MainSectionPopular from './MainSectionPopular.vue';
import AppJournal from './AppJournal.vue';
import MainSectionCollection from './MainSectionCollection.vue'; MainSectionCollection
import MainSectionNews from './MainSectionNews.vue'; 
export default {
    components: { MainSectionPopular, AppJournal, MainSectionCollection, MainSectionNews }
}
</script>

<style lang="scss" scoped>
main{
}
</style>
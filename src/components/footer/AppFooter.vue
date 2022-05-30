<template>
  <footer>
      <FooterSubscribe />
      <FooterImgBanner />
      <FooterLinks />
      <FooterRights />
  </footer>
</template>

<script>
import FooterSubscribe from './FooterSubscribe.vue';
import FooterImgBanner from './FooterImgBanner.vue';
import FooterLinks from './FooterLinks.vue';
import FooterRights from './FooterRights.vue';
export default {
    components: { FooterSubscribe, FooterImgBanner, FooterLinks, FooterRights }
}
</script>

<style>

</style>
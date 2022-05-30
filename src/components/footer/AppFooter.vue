<template>
  <footer>
      <FooterSubscribe />
      <FooterImgBanner />
      <FooterLinks />
  </footer>
</template>

<script>
import FooterSubscribe from './FooterSubscribe.vue';
import FooterImgBanner from './FooterImgBanner.vue';
import FooterLinks from './FooterLinks.vue';
export default {
    components: { FooterSubscribe, FooterImgBanner, FooterLinks }
}
</script>

<style>

</style>
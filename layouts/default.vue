<template>
  <div>
    <a-layout>
      <!-- Header -->
      <a-layout-header :class="headerBg">
        <Header />
      </a-layout-header>

      <!-- Content -->
      <a-layout-content :class="contentBg">
        <Nuxt />
      </a-layout-content>

      <!-- Footer -->
      <a-layout-footer>Footer</a-layout-footer>
    </a-layout>
  </div>
</template>

<script>
export default {
  computed: {
    contentBg() {
      try {
        return $nuxt.$route.path === "/" ? "nice-bg" : "white-bg";
      } catch (error) {
        return "white-bg";
      }
    },
    headerBg() {
      try {
        return $nuxt.$route.path === "/" ? "no-bg" : "nice-bg";
      } catch (error) {
        return "white-bg";
      }
    }
  }
};
</script>

<style lang="scss">
@import "@/assets/scss/main.scss";
</style>
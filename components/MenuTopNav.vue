<template>
  <div v-if="visible" class="header--menu-top-nav">
    <nuxt-link to="/blog">
      <a-button class="btn--nav" ghost>Blog</a-button>
    </nuxt-link>
  </div>
</template>

<script>
export default {
  computed: {
    visible() {
      let bool = true;

      try {
        bool = $nuxt.$route.path !== "/blog";
      } catch (error) {
        bool = true;
      }

      return bool;
    }
  }
};
</script>
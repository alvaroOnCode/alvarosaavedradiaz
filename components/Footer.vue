<template>
  <p>
    &copy; {{ year }} Álvaro Saavedra Díaz 🧑‍💻 |
    Made with JavaScript and a lot of
    <a-icon class="footer__icon-heart" type="heart" />
  </p>
</template>

<script>
export default {
  name: "Footer",
  computed: {
    year: () => {
      const d = new Date();
      return d.getFullYear();
    }
  }
};
</script>
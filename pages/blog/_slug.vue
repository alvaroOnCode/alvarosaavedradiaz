<template>
  <section class="container">
    <article class="container-article">
      <a-row type="flex" justify="center">
        <a-col :span="16">
          <img :src="article.img" :alt="article.alt" />

          <h1 class="heading-secondary">{{ article.title }}</h1>
          <h2 class="description">{{ article.description }}</h2>

          <p class="date">Actualizado el {{ formatDate(article.updatedAt) }}</p>

          <nuxt-content class="paragraph" :document="article" />

          <a-avatar v-for="(tag, index) in article.tags" :key="index" :src="url(tag)" size="large" />

          <prev-next :prev="prev" :next="next" />
        </a-col>
      </a-row>
    </article>
  </section>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const article = await $content("articles", params.slug).fetch();

    const [prev, next] = await $content("articles")
      .only(["title", "slug"])
      .sortBy("createdAt", "asc")
      .surround(params.slug)
      .fetch();

    return {
      article,
      prev,
      next
    };
  },

  methods: {
    formatDate(date) {
      const options = { year: "numeric", month: "long", day: "numeric" };
      return new Date(date).toLocaleDateString("es", options);
    },

    url(tag) {
      return require(`@/assets/images/brands/${tag}.png`);
    }
  }
};
</script>

<style lang="scss">
@import "@/assets/scss/pages/_article.scss";
</style>
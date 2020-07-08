<template>
  <section class="container">
    <article class="container-article">
      <a-row class="container-article__heading" type="flex" justify="center">
        <a-col :span="16">
          <a-row type="flex" justify="space-between">
            <a-col :span="7" class="container-article__heading--img">
              <img :src="article.img" :alt="article.alt" />
            </a-col>

            <a-col :span="16">
              <h1 class="heading-secondary">{{ article.title }}</h1>
              <h2 class="description">🧑‍💻 {{ article.description }}</h2>

              <p class="date">Actualizado el {{ formatDate(article.updatedAt) }}</p>
            </a-col>
          </a-row>
        </a-col>
      </a-row>

      <a-row class="container-article__content" type="flex" justify="center">
        <a-col :span="16">
          <nuxt-content class="paragraph" :document="article" />

          <a-avatar
            v-for="(tag, index) in article.tags"
            :key="index"
            :src="url(tag)"
            class="container-article__content--avatar"
            size="large"
          />

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
<template>
  <section class="container">
    <article class="container-article">
      <!-- Heading -->
      <a-row class="container-article__heading" type="flex" justify="center">
        <a-col :span="16">
          <a-row type="flex" justify="space-between">
            <!-- Image -->
            <a-col :span="7" class="container-article__heading--img">
              <img :src="article.img" :alt="article.alt" />
            </a-col>

            <!-- Title and description -->
            <a-col :span="16">
              <a-row>
                <a-col :span="24">
                  <h1 class="heading-secondary">{{ article.title }}</h1>
                  <h2 class="description">🧑‍💻 {{ article.description }}</h2>

                  <p class="date">📅 Actualizado el {{ formatDate(article.updatedAt) }}</p>
                </a-col>
              </a-row>

              <a-row>
                <a-col :span="24">
                  <!-- Tags -->
                  <tag-avatars :size="'large'" :tags="article.tags" />
                </a-col>
              </a-row>
            </a-col>
          </a-row>

          <a-divider />
        </a-col>
      </a-row>

      <!-- Content -->
      <a-row class="container-article__content" type="flex" justify="center">
        <a-col :span="16">
          <!-- Text -->
          <nuxt-content class="paragraph" :document="article" />

          <a-divider />

          <!-- Prev and Next -->
          <a-row>
            <a-col :span="24">
              <prev-next :prev="prev" :next="next" />
            </a-col>
          </a-row>
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
    }
  },

  head() {
    return {
      title: `Álvaro Saavedra 🧑‍💻 ${this.article.title}`,
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        {
          hid: "description",
          name: "description",
          content: this.article.description
        },
        {
          hid: "keywords",
          name: "keywords",
          content: this.article.tags
        },
        {
          hid: "author",
          name: "author",
          content: "Álvaro Saavedra Díaz"
        }
      ]
    };
  }
};
</script>
<template>
  <div class="container">
    <div class="container-blog">
      <!-- Title and Subtitle -->
      <a-row class="container-blog__text-block" type="flex" justify="center">
        <a-col>
          <h1 class="heading-secondary">Blog</h1>
        </a-col>
      </a-row>

      <a-row class="container-blog__articles" type="flex">
        <a-col
          v-for="article of articles"
          :key="article.slug"
          :span="6"
          class="container-blog__article"
          hoverable
        >
          <NuxtLink :to="{ name: 'blog-slug', params: { slug: article.slug } }">
            <a-card hoverable>
              <img :alt="article.title" :src="article.img" slot="cover" />

              <a-card-meta :title="article.title" class="heading-tertiary">
                <template slot="description">
                  <p class="paragraph">{{ article.description }}</p>
                </template>
              </a-card-meta>
            </a-card>
          </NuxtLink>
        </a-col>
      </a-row>
    </div>
  </div>
</template>

<script>
export default {
  async asyncData({ $content, params }) {
    const articles = await $content("articles", params.slug)
      .only(["title", "description", "img", "slug"])
      .sortBy("createdAt", "asc")
      .fetch();

    return {
      articles
    };
  },

  methods: {
    url(tag) {
      return require(`@/assets/images/brands/${tag}.png`);
    }
  }
};
</script>
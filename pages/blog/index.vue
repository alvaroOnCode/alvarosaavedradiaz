<template>
  <div class="container">
    <div class="container-blog">
      <!-- Title and Subtitle -->
      <a-row class="container-blog__text-block" type="flex" justify="center">
        <a-col>
          <h1 class="heading-secondary">Blog</h1>
        </a-col>
      </a-row>

      <a-row v-for="article of articles" :key="article.slug">
        <a-col>
          <NuxtLink :to="{ name: 'blog-slug', params: { slug: article.slug } }">
            <img :src="article.img" />
            <div>
              <h2>{{ article.title }}</h2>
              <p>{{ article.description }}</p>
            </div>
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
  }
};
</script>

<style lang="scss">
@import "@/assets/scss/pages/_blog.scss";
</style>
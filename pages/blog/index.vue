<template>
  <div class="container">
    <div class="container-blog">
      <!-- Title and Subtitle -->
      <a-row class="container-blog__text-block" type="flex" justify="center">
        <a-col>
          <h1 class="heading-secondary">Blog</h1>
        </a-col>
      </a-row>

      <!-- Tags -->
      <div class="container-blog__tags">
        <a-tag
          v-for="(t, i) in tags"
          :key="i"
          class="container-blog__tag"
          color="#73d1ff"
        >{{ t.name }}</a-tag>
      </div>

      <a-divider />

      <!-- Articles -->
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
              <!-- Image -->
              <img :alt="article.title" :src="article.img" slot="cover" />

              <!-- Meta -->
              <a-card-meta :title="article.title" class="heading-tertiary">
                <template slot="description">
                  <p class="paragraph">
                    {{ article.description }}
                    <a-icon type="caret-right" />
                  </p>
                </template>
              </a-card-meta>

              <a-divider></a-divider>

              <!-- Tags -->
              <tag-avatars :size="'small'" :tags="article.tags" />
            </a-card>
          </NuxtLink>
        </a-col>
      </a-row>
    </div>
  </div>
</template>

<script>
import { tags } from "../../utils/tags";

export default {
  async asyncData({ $content, params }) {
    const articles = await $content("articles", params.slug)
      .sortBy("createdAt", "asc")
      .fetch();

    return {
      articles
    };
  },

  data: () => ({
    tags
  }),

  methods: {
    url(tag) {
      return require(`@/assets/images/brands/${tag}.png`);
    }
  },

  head() {
    return {
      title: "Álvaro Saavedra Díaz 🧑‍💻 Software Developer",
      meta: [
        // hid is used as unique identifier. Do not use `vmid` for it as it will not work
        {
          hid: "description",
          name: "description",
          content:
            "Página web de Álvaro Saavedra (@alvaroOnCode), donde encontrarás información personal, profesional y artículos de desarrollo de software."
        }
      ]
    };
  }
};
</script>
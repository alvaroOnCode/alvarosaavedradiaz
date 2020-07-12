<template>
  <a-row v-if="checkTags(tags)" class="container-article__avatars" type="flex" justify="start">
    <a-col
      v-for="(tag, index) in tags"
      :key="index"
      :span="1"
      class="container-article__avatar-container"
    >
      <a-tooltip placement="bottomLeft">
        <template slot="title">
          <span>{{ tag }}</span>
        </template>

        <a-avatar :src="url(tag)" class="container-article__avatar" :size="size" />
      </a-tooltip>
    </a-col>
  </a-row>

  <a-tooltip v-else placement="bottomLeft">
    <template slot="title">
      <span>Miscelánea</span>
    </template>

    <div class="container-article__misc">
      <span class="container-article__misc--emoji">🤔</span>
    </div>
  </a-tooltip>
</template>

<script>
export default {
  props: {
    size: {
      default: "small",
      type: String,
      required: true
    },

    tags: {
      type: Array,
      required: true
    }
  },

  methods: {
    checkTags(tags) {
      try {
        tags.map(t => {
          return require(`@/assets/images/brands/${t}.png`);
        });
      } catch (error) {
        return false;
      }

      return true;
    },

    url(tag) {
      return require(`@/assets/images/brands/${tag}.png`);
    }
  }
};
</script>
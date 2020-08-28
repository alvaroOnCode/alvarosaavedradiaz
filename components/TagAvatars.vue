<template>
  <a-row v-if="checkTags()" class="container-article__avatars" type="flex" justify="start">
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
      required: true,
    },

    tags: {
      type: Array,
      required: true,
    },
  },

  methods: {
    checkTags() {
      const founds = [];

      this.tags.forEach((t) => {
        Object.keys(this.$tags).forEach((item) => {
          if (item === t) {
            founds.push(this.$tags[item]);
          }
        });
      });

      return founds.length > 0;
    },

    url(tag) {
      let found;

      Object.keys(this.$tags).forEach((item) => {
        if (item === tag) {
          found = this.$tags[item];
        }
      });

      return found ? found.img : "";
    },
  },
};
</script>

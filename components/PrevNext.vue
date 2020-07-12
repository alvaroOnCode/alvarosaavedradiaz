<template>
  <a-row class="prev-next__container" type="flex" justify="space-between">
    <!-- Previous -->
    <a-col>
      <NuxtLink
        v-if="prev"
        :to="{ name: 'blog-slug', params: { slug: prev.slug } }"
        class=""
      >
        <a-icon type="caret-left" />
        {{ prev.title }}
      </NuxtLink>
    </a-col>

    <!-- Next -->
    <a-col>
      <NuxtLink
        v-if="next"
        :to="{ name: 'blog-slug', params: { slug: next.slug } }"
        class=""
      >
        {{ next.title }}
        <a-icon type="caret-right" />
      </NuxtLink>
    </a-col>
  </a-row>
</template>

<script>
export default {
  props: {
    prev: {
      type: Object,
      default: () => null
    },
    next: {
      type: Object,
      default: () => null
    }
  }
};
</script>
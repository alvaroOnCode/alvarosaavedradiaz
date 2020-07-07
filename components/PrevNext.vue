<template>
  <a-row type="flex" justify="space-between">
    <!-- Previous -->
    <a-col>
      <NuxtLink
        v-if="prev"
        :to="{ name: 'blog-slug', params: { slug: prev.slug } }"
        class="text-primary font-bold hover:underline"
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
        class="font-bold hover:underline"
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
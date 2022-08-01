<template>
  <div class="post">
    {{ blog }}

    <nuxt-content :document="blog"></nuxt-content>
  </div>
</template>

<script>
export default {
  head() {},
  async asyncData({ $content, params }) {
    const blog = await $content('blog', params.slug).fetch()
    return { blog }
  },
}
</script>

<style scoped></style>

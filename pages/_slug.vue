<template>
  <div class="post">
    <v-card class="article-card" elevation="0">
      <v-card-title>
        <h1>
          {{ blog.title }}
        </h1>
      </v-card-title>

      <v-card-text>
        <hr class="my-3" />
        <article class="blog-content">
          <nuxt-content :document="blog"></nuxt-content>
        </article>
      </v-card-text>
    </v-card>
  </div>
</template>

<script>
export default {
  head() {},
  async asyncData({ $content, params }) {
    const blog = await $content('blogs', params.slug).fetch()
    return { blog }
  },
}
</script>

<style scoped>
.article-card {
  width: 85%;
  margin: auto;
}
.blog-content {
  font-size: 18px;
  text-align: justify;
  line-height: 1.5;
}
</style>

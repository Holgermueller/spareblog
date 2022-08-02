<template>
  <div class="post">
    <v-card class="article-card" elevation="0">
      <v-card-title>
        <h1>
          {{ blog.title }}
        </h1>
      </v-card-title>

      <v-card-text>
        <nuxt-content :document="blog"></nuxt-content>
      </v-card-text>

      <v-card-actions>
        <v-chip outlined to="/">
          <v-icon left>mdi-arrow-left</v-icon> Back
        </v-chip>
      </v-card-actions>
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
</style>

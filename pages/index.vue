<template>
  <div id="home">
    <p>
      {{ blogs[0] }}
    </p>
    <v-card>
      <v-card-title class="headline">
        <p>
          {{ blogs[0].title }}
        </p>
        <v-spacer></v-spacer>
        <p>
          {{ formatDate(blogs[0].date) }}
        </p>
      </v-card-title>
      <v-card-text>
        <hr class="my-3" />

        {{ blogs[0].body }}
      </v-card-text>
      <v-card-actions> </v-card-actions>
    </v-card>
  </div>
</template>

<script>
export default {
  name: 'IndexPage',

  name: 'DefaultLayout',
  async asyncData({ $content }) {
    const blogs = await $content('blogs').sortBy('date', 'desc').fetch()
    return {
      blogs,
    }
  },

  methods: {
    formatDate(date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' }
      return new Date(date).toLocaleDateString('en', options)
    },
  },
}
</script>

<style scoped></style>

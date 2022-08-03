<template>
  <div>
    <div v-for="(blog, index) in blogs" :key="index">
      <v-hover v-slot:default="{ hover }">
        <v-card class="archive-card" :elevation="hover ? 12 : 0">
          <v-card-title class="card-title">
            <h5>
              {{ blog.title }}
            </h5>
            <v-spacer></v-spacer>
            <h5>
              {{ blog.createdAt | formatDate }}
            </h5>
          </v-card-title>
          <v-card-subtitle>
            <hr class="my-3" />
          </v-card-subtitle>
          <v-card-text> description here </v-card-text>
          <v-card-actions>
            <nuxt-link :to="{ name: 'slug', params: { slug: blog.slug } }">
              <v-chip outlined>
                Keep reading
                <v-icon right>mdi-arrow-right</v-icon>
              </v-chip>
            </nuxt-link>
          </v-card-actions>
        </v-card>
      </v-hover>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Archives',

  head() {
    return {
      title: 'Archives',
    }
  },

  async asyncData({ $content, params }) {
    const blogs = await $content('blogs', params.slug)
      .sortBy('createdAt', 'desc')
      .fetch()
    return {
      blogs,
    }
  },

  filters: {
    formatDate(date) {
      const options = { year: 'numeric', month: 'long', day: 'numeric' }
      return new Date(date).toLocaleDateString('en', options)
    },
  },
}
</script>

<style scoped>
.archive-card {
  width: 85%;
  margin: 5px auto;
}
a {
  text-decoration: none;
}
</style>

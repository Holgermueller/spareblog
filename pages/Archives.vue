<template>
  <div id="previousPage">
    <ArchivesHeader />

    <div class="previous-container" v-for="(blog, index) in blogs" :key="index">
      <v-hover v-slot:default="{ hover }">
        <v-card class="archive-card" :elevation="hover ? 12 : 0" tile>
          <v-card-title class="card-title">
            <h5>
              {{ blog.title }}
            </h5>
            <v-spacer></v-spacer>
            <h5>
              {{ blog.date | formatDate }}
            </h5>
          </v-card-title>
          <v-card-subtitle>
            <hr class="my-3" />
          </v-card-subtitle>
          <v-card-text>
            <section>
              <h4>
                {{ blog.description }}
              </h4>
            </section>
          </v-card-text>
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
import ArchivesHeader from '../components/ArchivesHeader.vue'

export default {
  name: 'Archives',

  head() {
    return {
      title: 'Archives',
    }
  },

  components: {
    ArchivesHeader,
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
#previousCard {
  margin: 5%auto;
}
.archive-card {
  width: 85%;
  margin: 5px auto;
}
a {
  text-decoration: none;
}
</style>

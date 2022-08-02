<template>
  <div id="home">
    <section id="newestPost">
      <v-card class="newest-blog" elevation="0">
        <v-card-title class="headline">
          <p>
            {{ blogs[0].title }}
          </p>

          <v-spacer></v-spacer>
          <p>
            {{ blogs[0].date | formatDate }}
          </p>
        </v-card-title>

        <v-card-subtitle>
          <p>Location</p>

          <p>Listening to</p>
          <hr class="my-3" />
        </v-card-subtitle>

        <v-card-text>
          <article>
            <nuxt-content :document="blogs[0]" />
          </article>
        </v-card-text>
      </v-card>
    </section>

    <section id="otherRecentPosts" class="other-recent-posts">
      <PreviousDisplay :blogs="blogs" />
    </section>
  </div>
</template>

<script>
import PreviousDisplay from '../components/Previous'

export default {
  name: 'Index',

  components: {
    PreviousDisplay,
  },

  name: 'DefaultLayout',
  async asyncData({ $content, params }) {
    const blogs = await $content('blogs', params.slug)
      .sortBy('date', 'desc')
      .fetch()
    return {
      blogs,
    }
  },

  methods: {
    determineTimeToRead(data) {
      const WordsPerMinute = 200
      let result = {}
    },
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
.newest-blog,
.other-recent-posts {
  width: 85%;
  margin: auto;
}
.divider {
  width: 95%;
  margin: auto;
}
</style>

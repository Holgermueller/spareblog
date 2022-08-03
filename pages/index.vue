<template>
  <div id="home">
    <section id="newestPost">
      <v-card class="newest-blog" elevation="0">
        <v-card-title class="headline">
          <h1>
            {{ blogs[0].title }}
          </h1>

          <v-spacer></v-spacer>

          <h1>
            {{ blogs[0].createdAt | formatDate }}
          </h1>
        </v-card-title>

        <v-card-subtitle>
          <br />
          <h4>Location</h4>

          <h4>Listening to</h4>
          <hr class="my-3" />
        </v-card-subtitle>

        <v-card-text>
          <article>
            <nuxt-content class="main-content" :document="blogs[0]" />
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
      .sortBy('createdAt', 'desc')
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
.main-content {
  font-size: 16px;
}
</style>

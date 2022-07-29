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
            {{ formatDate(blogs[0].date) }}
          </p>
        </v-card-title>
        <v-card-text>
          <hr class="my-3" />

          <article>
            <nuxt-content :document="blogs[0]"></nuxt-content>
          </article>
        </v-card-text>
        <v-card-actions> </v-card-actions>
      </v-card>
    </section>

    <section id="otherRecentPosts" class="other-recent-posts">
      <h2>other recent posts appear here</h2>
      <v-container>
        <v-row>
          <v-col>
            <v-hover v-slot:default="{ hover }">
              <v-card :elevation="hover ? 12 : 0" class="recent-post">
                <v-card-title> title </v-card-title>
                <hr />
                <v-card-text> text </v-card-text>
              </v-card>
            </v-hover>
          </v-col>
          <v-col>
            <v-hover v-slot:default="{ hover }">
              <v-card :elevation="hover ? 12 : 0" class="recent-post">
                <v-card-title> title </v-card-title>
                <hr />
                <v-card-text> text </v-card-text>
              </v-card>
            </v-hover>
          </v-col>
          <v-col>
            <v-hover v-slot:default="{ hover }">
              <v-card :elevation="hover ? 12 : 0" class="recent-post">
                <v-card-title> title </v-card-title>
                <hr />
                <v-card-text> text </v-card-text>
              </v-card>
            </v-hover>
          </v-col>
        </v-row>
      </v-container>
    </section>
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

<style scoped>
.newest-blog {
  width: 95%;
  margin: auto;
}

.other-recent-posts {
  width: 95%;
  margin: auto;
}
</style>

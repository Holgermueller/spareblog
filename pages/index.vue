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
      <v-container>
        <v-row>
          <v-col v-for="(blog, index) in blogs.slice(1, 4)" :key="index">
            <v-hover v-slot:default="{ hover }">
              <v-card :elevation="hover ? 12 : 0" class="recent-post">
                <v-card-title>
                  <h6>
                    {{ blog.title }}
                  </h6>
                  <v-spacer></v-spacer>
                  <h6>
                    {{ formatDate(blog.date) }}
                  </h6>
                </v-card-title>
                <v-divider class="divider"></v-divider>
                <v-card-text>
                  <article>
                    <nuxt-content :document="blog" />
                  </article>
                </v-card-text>
                <v-card-actions>
                  <v-spacer></v-spacer>
                  <v-chip outlined>
                    Keep reading <v-icon right>mdi-arrow-right</v-icon>
                  </v-chip>
                </v-card-actions>
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
  name: 'Index',

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

    // determineTimeToRead(data) {
    //   const WordsPerMinute = 200
    //   let result: any = {}
    // },
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

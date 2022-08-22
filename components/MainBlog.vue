<template>
  <div id="mainBlog">
    <v-card class="newest-blog" tile>
      <v-img class="align-end" height="400px" width="100%" :src="blogs[0].img">
        <v-card-title class="headline">
          <h1>
            {{ blogs[0].title }}
          </h1>

          <v-spacer></v-spacer>

          <h1>
            {{ blogs[0].date | formatDate }}
          </h1>
        </v-card-title>
      </v-img>

      <v-card-subtitle>
        <br />
        <h4>Location: {{ blogs[0].location }}</h4>

        <h4>Listening to: {{ blogs[0].listeningTo }}</h4>
        <hr class="my-3" />
      </v-card-subtitle>

      <v-card-text>
        <article class="main-content">
          <nuxt-content :document="blogs[0]" />
        </article>
      </v-card-text>
    </v-card>
  </div>
</template>

<script>
export default {
  name: 'MainBlog',

  props: {
    blogs: {
      type: Array,
    },
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
.newest-blog {
  margin: 5% auto;
}
.main-content {
  font-size: 18px;
  text-align: justify;
  line-height: 1.5;
}
</style>

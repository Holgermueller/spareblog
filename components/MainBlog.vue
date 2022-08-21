<template>
  <div id="mainBlog">
    <v-card class="newest-blog" tile>
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

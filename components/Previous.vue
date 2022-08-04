<template>
  <div id="previous">
    <v-container>
      <v-row>
        <v-col v-for="(blog, index) in blogs.slice(1, 4)" :key="index">
          <v-hover v-slot:default="{ hover }">
            <v-card :elevation="hover ? 12 : 0" class="recent-post">
              <v-card-title>
                <h3>
                  {{ blog.title }}
                </h3>
                <v-spacer></v-spacer>
                <h3>
                  {{ blog.createdAt | formatDate }}
                </h3>
              </v-card-title>
              <v-card-subtitle>
                <hr class="my-3" />
              </v-card-subtitle>
              <v-card-text>
                <article>
                  <nuxt-content :document="blog" />
                </article>
              </v-card-text>
              <v-card-actions>
                <v-spacer></v-spacer>
                <nuxt-link :to="{ name: 'slug', params: { slug: blog.slug } }">
                  <v-chip outlined>
                    Keep reading <v-icon right>mdi-arrow-right</v-icon>
                  </v-chip>
                </nuxt-link>
              </v-card-actions>
            </v-card>
          </v-hover>
        </v-col>
      </v-row>
    </v-container>
  </div>
</template>

<script>
export default {
  name: 'PreviousDisplay',

  props: {
    blogs: {
      type: Array,
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
a {
  text-decoration: none;
}
</style>

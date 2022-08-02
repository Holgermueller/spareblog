<template>
  <div id="previous">
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
                  {{ blog.date | formatDate }}
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
                <nuxt-link
                  :to="{ name: 'blog-slug', params: { slug: blog.slug } }"
                >
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
.divider {
  width: 95%;
  margin: auto;
}
a {
  text-decoration: none;
}
</style>

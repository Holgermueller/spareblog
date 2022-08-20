<template>
  <div id="home">
    <section id="newestPost" class="newest-blog">
      <MainBlog :blogs="blogs" />
    </section>

    <section id="otherRecentPosts" class="other-recent-posts">
      <PreviousDisplay :blogs="blogs" />
    </section>
  </div>
</template>

<script>
import MainBlog from '../components/MainBlog.vue'
import PreviousDisplay from '../components/Previous'

export default {
  name: 'Index',

  components: {
    MainBlog,
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
}
</script>

<style scoped>
.newest-blog,
.other-recent-posts {
  width: 85%;
  margin: auto;
}
</style>

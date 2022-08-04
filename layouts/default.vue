<template>
  <v-app dark>
    <v-main class="app">
      <v-container>
        <v-app-bar elevation="0" color="#31708e" app dark>
          <nuxt-link to="/">
            <h1>
              <i>Holger Mueller</i>
            </h1>
          </nuxt-link>

          <v-spacer></v-spacer>
          <div v-for="(link, i) in navArray" :key="i">
            <nuxt-link :to="link.path">
              <h3>
                <span class="mr-6">
                  {{ link.linkName }}
                </span>
              </h3>
            </nuxt-link>
          </div>
        </v-app-bar>
        <Nuxt />
      </v-container>
    </v-main>

    <v-footer absolute app color="#31708e" dark>
      <span
        >&copy; {{ new Date().getFullYear() }} Holger Mueller &middot; Built
        with <a href="https://nuxtjs.org/">Nuxtjs</a>
      </span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: 'default',
  data: () => ({
    navArray: [
      { linkName: 'About', path: '/about' },
      { linkName: 'Archives', path: '/archives' },
      { linkName: 'Contact', path: '/contact' },
    ],
  }),
}
</script>

<style scoped>
.app {
  /*image from pexels, photographer: Sasha Martynov*/
  background-image: url('../static/backgroundimage.png');
  background-size: auto;
  background-repeat: repeat;
}
a {
  text-decoration: none;
  color: white !important;
}
</style>

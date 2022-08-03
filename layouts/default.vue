<template>
  <v-app dark>
    <v-main class="app">
      <v-container>
        <v-app-bar elevation="0" color="#31708e" app dark>
          <v-btn to="/" elevation="0" text dark>
            <h1>Holger Mueller</h1>
          </v-btn>

          <v-spacer></v-spacer>
          <div v-for="(button, i) in navArray" :key="i">
            <v-btn :to="button.buttonLink" elevation="0" text block>
              <span class="mr-2">
                {{ button.buttonName }}
              </span>
            </v-btn>
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
      { buttonName: 'About', buttonLink: '/about' },
      { buttonName: 'Archives', buttonLink: '/archives' },
      { buttonName: 'Contact', buttonLink: '/contact' },
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
  color: white;
}
</style>

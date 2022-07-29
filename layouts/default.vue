<template>
  <v-app dark>
    <v-main>
      <v-container>
        <v-app-bar elevation="0" app>
          <v-btn to="/" elevation="0">
            <h1>Holger Mueller</h1>
          </v-btn>

          <v-spacer></v-spacer>
          <v-btn elevation="0" class="no-active" to="/about">About</v-btn>
          <v-btn elevation="0" class="no-active" to="/contact">Contact</v-btn>
        </v-app-bar>
        <Nuxt />
      </v-container>
    </v-main>

    <v-footer app>
      <span
        >&copy; {{ new Date().getFullYear() }} Holger Mueller &middot; Built
        with Nuxtjs</span
      >
    </v-footer>
  </v-app>
</template>

<script>
export default {}
</script>

<style scoped>
a {
  text-decoration: none;
}
</style>

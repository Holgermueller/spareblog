<template>
  <v-app dark>
    <v-main>
      <v-container>
        <v-app-bar app>
          <h1>Holger Mueller</h1>
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
export default {
  name: 'DefaultLayout',
  data: () => ({}),
}
</script>

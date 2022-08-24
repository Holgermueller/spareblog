<template>
  <div id="archivesHeader">
    <v-card class="header">
      <v-img
        class="white--text align-end"
        height="400px"
        src="/images/archives.png"
      >
        >
        <v-card-title>
          <h1 class="display-4">Archives</h1>
        </v-card-title>
        <hr class="my-3" />
        <v-card-subtitle>
          <h4 class="subtitle-1">Tales of yore</h4>
          <h6>Photo by Pixabay via Pexels</h6>
        </v-card-subtitle></v-img
      >
    </v-card>
  </div>
</template>

<script>
export default {
  name: 'ArchivesHeader',
}
</script>

<style scoped>
.header {
  width: 85%;
  margin: 5% auto;
}
</style>

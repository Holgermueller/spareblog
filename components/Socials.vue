<template>
  <div id="socials">
    <v-card class="connections-display" elevation="0" tile>
      <v-card-title>
        <h3>Connect on my socials</h3>
      </v-card-title>
      <v-card-text>
        <v-container>
          <v-row>
            <v-col v-for="(connection, index) in connections" :key="index">
              <v-btn
                :href="connection.link"
                target="_blank"
                class="social-link"
                text
                block
              >
                <v-icon> {{ connection.connection_class }}</v-icon>
                <span class="connection-name">{{ connection.name }}</span>
              </v-btn>
            </v-col>
          </v-row>
        </v-container>
      </v-card-text>
    </v-card>
  </div>
</template>

<script>
export default {
  name: 'SocialConnects',
  data: () => ({
    connections: [
      {
        name: 'Github',
        connection_class: 'mdi mdi-github',
        link: 'https://github.com/Holgermueller',
      },
      {
        name: 'LinkedIn',
        connection_class: 'mdi mdi-linkedin',
        link: 'https://www.linkedin.com/in/holger-mueller-75855114a/',
      },
    ],
  }),
}
</script>

<style scoped>
.connections-display {
  width: 85%;
  margin-left: auto;
  margin-right: auto;
  background-color: #f7f9fb;
}
.social-link:hover {
  background-color: #31708e;
  color: #f7f9fb;
}
</style>

<template>
  <v-app>
    <v-content>
      <v-container class="grey lighten-4" fluid>
        <v-layout row wrap>
          <v-flex xs12>
            <Home />
          </v-flex>
        </v-layout>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import Home from "./components/Home.vue";

export default {
  components: {
    Home
  }
};
</script>

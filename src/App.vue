<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >
      <div class="d-flex align-center">
        <h2>SpaceX Timeline</h2>
      </div>

      <v-spacer></v-spacer>

    </v-app-bar>

    <v-main>

    </v-main>
  </v-app>
</template>

<script>
import axios from "axios";
export default {
  name: "App",

  components: {},

  data: () => ({
    launches: [],
  }),
  async created() {
    const { data } = axios.get("https://api.spacexdata.com/v4/launches");

    data.forEach(launch => {
      this.launches.push(launch);
    });
  },
};
</script>

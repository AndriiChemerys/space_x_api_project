<template>
  <v-app>
    <!-- <v-app-bar app color="primary" dark>
      <div class="d-flex align-center">
        <h2>SpaceX Launches</h2>
      </div>

      <v-spacer></v-spacer>
    </v-app-bar> -->
    <v-content class="hero-image">
      <div class="center">
        <h2>SpaceX Launches Timeline</h2>
        <!-- <p>Launches Timeline</p> -->
        <p>History:</p>
      </div>
    </v-content>
    <v-content>
      <SpacexCarousel/>
    </v-content>
    <v-content >
      <v-container >
        <v-timeline v-if="launches.length > 0">
          <LaunchTimeLineItem
            v-for="launch in launches"
            :key="launch.flight_number"
            :launch="launch"
          />
        </v-timeline>
      </v-container>
    </v-content>
  </v-app>
</template>

<script>
import axios from "axios";
import LaunchTimeLineItem from "./components/LaunchTimeLineItem";
import SpacexCarousel from "./components/SpacexCarousel";

export default {
  name: "App",
  components: {
    LaunchTimeLineItem,
    SpacexCarousel,
  },
  data: () => ({
    launches: [],
  }),
  async created() {
    const { data } = await axios.get(
      "https://api.spacexdata.com/v3/launches/past"
    );

    data.forEach(launch => {
      this.launches.push(launch);
    });
  },
};
</script>
<style>
.hero-image {
  background-image: url("img/SpaceX_img2.png");
  /* width: 100%; */
  /* width: 100vw; */
  height: 100vh;
  width: 100%;
  background-position: center;
  /* background-repeat: no-repeat;  */
  /* background-position: 0% 0%; */
  background-size: contain;
  background-repeat: no-repeat;
  background-attachment: fixed;
}

.center {
  font-family: "Lucida Sans", "Lucida Sans Regular", "Lucida Grande",
    "Lucida Sans Unicode", Geneva, Verdana, sans-serif;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  color: white;
  /* display: block; */
}

.child {
  display: block;
}
</style>

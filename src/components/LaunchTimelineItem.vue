<template>
  <v-timeline class="timeline" :reverse="reverse" :dense="$vuetify.breakpoint.smAndDown">
    <v-timeline-item large class="timeline__item" v-for="n in 2" :key="n">
      <template v-slot:icon>
        <v-avatar>
          <img class="timeline__img" :src="launch.links.mission_patch_small" alt="">
        </v-avatar>
      </template>
      <template>
        <span slot="opposite">
          {{launchDate}}
        </span>
      </template>
      <v-card class="elevation-2">
        <v-card-title class="headline">
          MISSION: {{launch.mission_name}}
        </v-card-title>
        <v-card-subtitle>
          ROCKET: {{launch.rocket.rocket_name}}
        </v-card-subtitle>
        <v-card-text>
          {{launch.details}}
        </v-card-text>
      </v-card>
    </v-timeline-item>
  </v-timeline>
</template>

<script>
  import moment from "moment";

  export default {
    props: ["launch"],
    computed: {
      launchDate() {
        return moment(this.launch.launch_date_local).format("MM/DD/YYYY");
      },
    },
  };
</script>

<style>
</style>
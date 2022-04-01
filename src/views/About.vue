<template>
  <v-container
    ><v-card
      ><v-card-title> ISBN: {{ info.isbn }}</v-card-title>
      <v-card-text v-for="author in info.authors" :key="author"
        >Autor: {{ author }}</v-card-text
      >
      <v-card-text>Stranice: {{ info.numberOfPages }}</v-card-text>
      <v-card-text>Autor: {{ info.mediaType }}</v-card-text>
      <v-card-text>Zemlja podrijetla: {{ info.country }}</v-card-text>
      <v-card-text v-if="info.characters"
        >Broj likova: {{ info.characters.length }}</v-card-text
      >
      <v-btn rounded color="error" @click="vrati()">NAZAD</v-btn>
    </v-card>
  </v-container>
</template>
<script>
import axios from "axios";

export default {
  name: "About",
  data() {
    return {
      info: [],
      isbn: this.$route.params.isbn,
    };
  },

  async mounted() {
    const podaci = await axios.get(`${this.isbn}`);

    this.info = podaci.data;
  },
  methods: {
    vrati() {
      this.$router.push("/");
    },
  },
};
</script>

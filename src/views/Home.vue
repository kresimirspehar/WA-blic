<template>
  <v-container style="margin-top: 10px; margin-bottom: 10px">
    <h1
      class="white--text mb-10 display-1 text-xs-center"
      style=" margin-bottom: 20px font-weight: 500; text-shadow: 3px 2px #000000"
    >
      WA - Blic
    </h1>
    <v-layout row wrap style>
      <kartica
        v-for="card in card"
        :id="card.isbn"
        :abt="card.name"
        :naziv="card.name"
        :aut="card.authors"
        :key="card.isbn"
      />
    </v-layout>
  </v-container>
</template>

<script>
import Kartica from "@/components/Kartica.vue";
import axios from "axios";

export default {
  name: "Home",
  components: {
    Kartica,
  },
  data() {
    return {
      card: [],
    };
  },
  async mounted() {
    const temp = await axios.get("https://www.anapioficeandfire.com/api/books");
    this.card = temp.data;
    console.log(this.card);
  },
};
</script>

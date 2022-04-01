<template>
  <v-layout row wrap style>
    <v-card
      class="text-xs-center ma-3"
      max-width="500"
      style="margin-top: 100px margin-left: 20px"
    >
      <router-link
        style="text decoration:none; color:black;"
        :to="{ name: 'About', params: { isbn: id } }"
      >
        <v-card-title> Naziv: {{ naziv }} </v-card-title>
      </router-link>
      <v-card-text> Autor: {{ aut[0] }} </v-card-text>
      <v-card-text> Datum: {{ abt }} </v-card-text>
      <v-card-actions>
        <router-link :to="{ name: 'About', params: { isbn: id } }">
          <v-btn rounded color="primary" dark>DETALJI</v-btn>
        </router-link>
      </v-card-actions>
    </v-card>
  </v-layout>
</template>
<script>
export default {
  name: "Kartica",
  props: {
    id: String,
    abt: String,
    naziv: String,
    aut: [],
  },
};
</script>

<style></style>

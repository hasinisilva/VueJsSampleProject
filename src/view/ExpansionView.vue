<template>
  <v-expansion-panels>
    <v-expansion-panel v-for="breed in breeds" :key="breed.id">
      <v-expansion-panel-header>{{ breed.name }}</v-expansion-panel-header>
      <v-expansion-panel-content>
        {{ breed.description }}
      </v-expansion-panel-content>
    </v-expansion-panel>
  </v-expansion-panels>
</template>

<script>
import axios from "axios";

export default {
  name: "GeneralDetailView",
  data() {
    return {
      breeds: []
    };
  },
  created() {
    axios
      .get(`https://api.thecatapi.com/v1/breeds`)
      .then(response => {
        this.breeds = response.data;
      })
      .catch(e => {
        this.errors.push(e);
      });
  }
};
</script>

<template>
  <v-row>
    <v-col v-for="breed in breeds" :key="breed.id" cols="12" sm="6" md="4">
      <CardComponent
        v-bind:title="breed.name"
        v-bind:description="breed.description"
      />
    </v-col>
  </v-row>
</template>

<script>
import axios from "axios";
import CardComponent from "../components/CardComponents.vue";

export default {
  name: "GeneralDetailView",
  data() {
    return {
      breeds: []
    };
  },
  components: {
    CardComponent
  },
  // this methos calls when the component is loading
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

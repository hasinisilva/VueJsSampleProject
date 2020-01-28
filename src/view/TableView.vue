<template>
  <v-simple-table>
    <template v-slot:default>
      <thead>
        <tr>
          <th class="text-left">Name</th>
          <th class="text-left">Origin</th>
          <th class="text-left">Temperament</th>
          <th class="text-left">Life Span</th>
        </tr>
      </thead>
      <tbody>
        <tr v-for="breed in breeds" :key="breed.id">
          <td>{{ breed.name }}</td>
          <td>{{ breed.origin }}</td>
          <td>{{ breed.temperament }}</td>
          <td>{{ breed.life_span }}</td>
        </tr>
      </tbody>
    </template>
  </v-simple-table>
</template>

<script>
import axios from "axios";

export default {
  name: "TableView",
  data() {
    return {
      breeds: []
    };
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

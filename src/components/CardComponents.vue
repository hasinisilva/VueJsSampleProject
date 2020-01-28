<template>
  <v-card>
    <v-card-title class="headline">{{ title }}</v-card-title>
    <v-card-subtitle>{{ description }}</v-card-subtitle>
  </v-card>
</template>

<script>
export default {
  name: "CardComponent",
  props: {
    title: String,
    description: String
  }
};
</script>

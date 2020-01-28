<template>
  <v-app id="app">
    <v-content>
      <MainLayout />
    </v-content>
  </v-app>
</template>

<script>
import MainLayout from "./view/MainLayout";
export default {
  name: "App",
  components: {
    MainLayout
  }
};
</script>

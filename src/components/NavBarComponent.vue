<template>
  <v-toolbar color="cyan" dark>
    <v-app-bar-nav-icon></v-app-bar-nav-icon>

    <v-toolbar-title>{{ title }}</v-toolbar-title>

    <v-spacer></v-spacer>

    <v-col cols="12" sm="6" md="4">
      <v-text-field
        class="mx-4"
        flat
        hide-details
        solo-inverted
        label="Search"
        v-model="search"
      >
        <v-btn icon>
          <v-icon>mdi-magnify</v-icon>
        </v-btn>
      </v-text-field>
    </v-col>
  </v-toolbar>
</template>

<script>
export default {
  name: "NavBarComponent",
  props: {
    title: String,
    search: { type: Function }
  }
};
</script>

<template>
  <v-card flat tile id="mainLayout">
    <v-toolbar color="cyan" dark>
      <v-app-bar-nav-icon></v-app-bar-nav-icon>
      <v-toolbar-title>Cat Breed</v-toolbar-title>
      <v-spacer></v-spacer>

      <v-col cols="12" sm="6" md="4">
        <input type="text" placeholder="Search a title..." v-model="search" />

        <div id="links">
          <span><router-link to="general-view">General View</router-link></span>
          <span><router-link to="table-view">Table View</router-link></span>
          <span
            ><router-link to="expansion-view">Expansion View</router-link></span
          >
        </div>
      </v-col>
    </v-toolbar>
    <router-view></router-view>
    <GeneralDetailView />
    <TableView />
    <ExpansionView />
  </v-card>
</template>

<script>
import GeneralDetailView from "./GeneralDetailView";
import TableView from "./TableView";
import ExpansionView from "./ExpansionView";
import VueRouter from "vue-router";
import Vue from "vue";
import axios from "axios";

const routes = [
  { path: "/table-view", component: TableView },
  { path: "/general-view", component: GeneralDetailView },
  { path: "/expansion-view", component: ExpansionView }
];

const router = new VueRouter({
  routes // short for `routes: routes`
});

export default {
  name: "MainLayout",
  props: {
    title: String
  },
  router,
  data() {
    return {
      search: null,
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
  // computed: {
  //   resultQuery() {
  //     if (this.search !== null) {
  //       return this.breeds.filter(item =>
  //         this.search
  //           .toLowerCase()
  //           .split(" ")
  //           .every(v => item.title.toLowerCase().includes(v))
  //       );
  //     } else {
  //       return this.breeds;
  //     }
  //   }
  // }
};
Vue.use(VueRouter);
</script>

<style>
#links {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  display: inline-flex;
}
span {
  padding: 10px;
}
</style>

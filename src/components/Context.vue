<template>
  <div>
    <Navigation @onChange="navigation" v-bind:items="items"/>
    <template v-for="(item,index) in results">
      <Tile v-bind:item="item" :key="index"/>
    </template>
  </div>
</template>


<script>
import Navigation from "./Navigation";
import Tile from "./Tile";

export default {
  name: "Context",
  components: {
    Navigation,
    Tile
  },
  methods: {
    navigation: function(item) {
      console.log("navigation", item.name);
    }
  },
  async created() {
    const response = await fetch(
      "https://api.themoviedb.org/3/movie/popular?api_key=7e12b66ea24703faef4d9209d109eb56&language=en-US&page=1"
    );
    const data = await response.json();
    this.results = data.results;
  },
  data() {
    return {
      results: null,
      items: [
        { name: "popular", active: true, id: 0 },
        { name: "top rated", active: false, id: 1 },
        { name: "upcoming", active: false, id: 2 },
        { name: "now playing", active: false, id: 3 }
      ]
    };
  }
};
</script>


<style>
</style>

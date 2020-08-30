<template>
  <div>
    <Navigation @onChange="navigation" v-bind:items="items"/>
    <template v-for="index in 4">
      <Tile :key="index"/>
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
  data: function() {
    return {
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

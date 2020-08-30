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
      this.callForData(item.url);
    },
    async callForData(url) {
      const response = await fetch(url);
      const data = await response.json();
      this.results = data.results;
    }
  },
  async created() {
    let url = null;
    this.items.forEach(element => {
      if (element.active) url = element.url;
    });
    this.callForData(url);
  },
  data() {
    const baseUrl = "https://api.themoviedb.org/3/movie/";
    const apik = "api_key=7e12b66ea24703faef4d9209d109eb56";
    const tailUrl = "&language=en-US&page=1";
    return {
      results: null,
      items: [
        {
          name: "popular",
          active: true,
          id: 0,
          url: baseUrl + "popular?" + apik + tailUrl
        },
        {
          name: "top rated",
          active: false,
          id: 1,
          url: baseUrl + "top_rated?" + apik + tailUrl
        },
        {
          name: "upcoming",
          active: false,
          id: 2,
          url: baseUrl + "upcoming?" + apik + tailUrl
        },
        {
          name: "now playing",
          active: false,
          id: 3,
          url: baseUrl + "now_playing?" + apik + tailUrl
        }
      ]
    };
  }
};
</script>


<style>
</style>

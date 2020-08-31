<template>
  <div>
    <Navigation @onChange="navigation" v-bind:items="items"/>
    <div class="wrapper-tiles">
      <div class="arrow">
        <span class="material-icons" v-on:click="scroll(0)" v-if="id>0">keyboard_arrow_left</span>
      </div>
      <div class="tiles" id="scroller">
        <Tile v-for="(item,index) in results" v-bind:item="item" :key="index" v-bind:id="index"/>
      </div>
      <div class="arrow">
        <span class="material-icons" v-on:click="scroll(1)">keyboard_arrow_right</span>
      </div>
    </div>
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
    },
    scroll(input) {
      if (input === 0 && this.$data.id > 0) {
        this.$data.id -= 3;
      } else if (input === 1) {
        this.$data.id += 3;
      } else {
        return;
      }
      let myElement = document.getElementById(this.$data.id);
      console.log("leftPos", this.$data.id);
      let leftPos = myElement.offsetLeft - 120;
      document.getElementById("scroller").scrollLeft = leftPos;
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
      id: 0,
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
.tiles {
  display: flex;
  width: 90vw;
  max-width: 865px;
  overflow: scroll;
  box-sizing: border-box;
  scroll-behavior: smooth;
}
.wrapper-tiles {
  display: flex;
  justify-content: center;
  align-items: center;
  margin-top: 90px;
}

.wrapper-tiles .material-icons {
  font-size: 40px;
  color: #747069;
  cursor: pointer;
  /* display: none; */
}

.arrow {
  width: 70px;
  display: flex;
  justify-content: center;
  align-items: center;
}

.tiles {
  scrollbar-width: none; /* For Firefox */
  -ms-overflow-style: none; /* For Internet Explorer and Edge */
}

.tiles::-webkit-scrollbar {
  width: 0px; /* For Chrome, Safari, and Opera */
}
</style>

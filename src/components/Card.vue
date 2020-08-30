<template>
  <div class="card-container">
    <Navigation/>
    <template v-for="index in 4">
      <Tile :key="index"/>
    </template>
    <div class="more">
      <span>View more</span>
    </div>
  </div>
</template>

<script>
import Navigation from "./Navigation";
import Tile from "./Tile";

export default {
  name: "Card",
  props: {
    msg: String
  },
  components: {
    Navigation,
    Tile
  }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.card-container {
  width: 1145px;
  height: 684px;
  background: #FFFFFF;
  box-shadow: 0px 7px 104px rgba(227, 206, 173, 0.74);
  border-radius: 10px;
}
</style>

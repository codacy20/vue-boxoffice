<template>
  <div class="tile-container">
    <div
      class="image"
      :style="{ backgroundImage: `url('https://image.tmdb.org/t/p/w200${this.item.poster_path}')` }"
    ></div>
    <div class="subs">
      <span id="title">{{item.title}}</span>
      <span id="date">{{item.release_date}}</span>
    </div>
  </div>
</template>

<script>
export default {
  name: "Tile",
  props: {
    item: Object
  }
};
</script>

<style>
.tile-container {
  height: 280px;
  min-width: 210px;
  background: #FFFFFF;
  border: 1px solid #E5E5E5;
  box-sizing: border-box;
  border-radius: 10px;
  box-sizing: border-box;
}
.image {
  height: 170px;
  border-top-left-radius: 10px;
  border-top-right-radius: 10px;
}
.subs {
  display: flex;
  justify-content: center;
  align-items: center;
  height: calc(270px - 170px);
  flex-direction: column;
}
#title {
  font-weight: bold;
  font-size: 20px;
  line-height: 25px;
  color: #000000;
}
#date {
  font-weight: normal;
  font-size: 16px;
  line-height: 20px;
  color: #747069;
}
</style>

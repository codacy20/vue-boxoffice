<template>
  <div class="card-container">
    <Context/>
    <div class="more" v-on:click="redirectToMovieDB">
      <span>View more</span>
    </div>
    <div class="love" v-on:click="redirect">
      <span>Made with</span>
      <span class="material-icons">favorite</span>
      <span>by amir</span>
    </div>
  </div>
</template>

<script>
import Context from "./Context";

export default {
  name: "Card",
  props: {
    msg: String
  },
  components: {
    Context
  },
  methods: {
    redirect() {
      window.open("https://twitter.com/RT_Amir", "_blank");
    },
    redirectToMovieDB() {
      window.open(
        "https://www.themoviedb.org/?ref=https://twitter.com/RT_Amir",
        "_blank"
      );
    }
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
  display: flex;
  align-items: center;
  flex-direction: column;
}
.more {
  margin-top: 50px;
  background: #EB6649;
  box-shadow: 0px 4px 10px rgba(235, 102, 73, 0.25);
  border-radius: 5px;
  width: 160px;
  height: 49px;
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}
.love {
  display: flex;
  width: 170px;
  justify-content: space-evenly;
  align-items: center;
  line-height: 40px;
  position: absolute;
  bottom: 1vh;
  cursor: pointer;
}
.love:hover .material-icons {
  color: red;
}
</style>

<template>
  <div id="app">
    <Card />
  </div>
</template>

<script>
import Card from "../components/Card";

export default {
  name: "App",
  components: {
    Card,
  },
};
</script>

<style>
#app {
  font-family: Muli;
  background: #f4efe5;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  user-select: none;
}
</style>

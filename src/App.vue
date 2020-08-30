<template>
  <div id="app">
    <Card msg="Hello Vue in CodeSandbox!"/>
  </div>
</template>

<script>
import Card from "./components/Card";

export default {
  name: "boxoffice",
  components: {
    Card
  }
};
</script>

<style>
#app {
  font-family: Muli;
  background: #F4EFE5;
  height: 98vh;
  display: flex;
  justify-content: center;
  align-items: center;
  user-select: none;
}
</style>

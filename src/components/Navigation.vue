<template>
  <div class="nav-container">
    <ul>
      <li
        class="item"
        v-for="item in items"
        :key="item.id"
        v-bind:class="{ active: item.active }"
        v-on:click="toggle(item)"
      >{{item.name}}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: "Navigation",
  props: {
    items: Array
  },
  methods: {
    toggle: function(item) {
      this.items.forEach(index => {
        index.active = false;
      });
      this.$emit("onChange", item);
      this.items[item.id].active = true;
    }
  }
};
</script>

<style>
.nav-container {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100%;
}
ul {
  max-width: 475px;
  display: flex;
  justify-content: space-around;
  align-items: center;
  flex-direction: row;
  width: 100%;
}
.item {
  list-style-type: none;
  cursor: pointer;
  color: #747069;
  border-radius: 6px;
  padding: 8px 22px;
  transition: 0.3s ease-in-out;
}

.item:hover {
  background: #FEF8EB;
}
.item.active {
  background: #FEF8EB;
  color: #000000;
}
.item::first-letter {
  text-transform: uppercase;
}
</style>

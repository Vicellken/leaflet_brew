<template>
  <div class="container-fluid" id="app">
    <brew />
  </div>
</template>

<script>
import Brew from "./components/Brew.vue";

export default {
  name: "app",
  components: {
    Brew
  }
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

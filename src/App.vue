<template>
  <div id="app">
    <NavFooter />
    <router-view />
  </div>
</template>


<script>
import NavFooter from "./components/NavFooter.vue";

export default {
  name: "app",
  components: {
    NavFooter
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

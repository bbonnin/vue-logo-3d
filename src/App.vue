<template>
  <div id="app">
    <!-- img src="./assets/logo.png"/ -->
    <Logo3D />
  </div>
</template>

<script>
import Logo3D from "./components/Logo3D.vue";

export default {
  name: "app",
  components: {
    Logo3D
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

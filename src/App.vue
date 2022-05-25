<template>
  <div id="app">
    <div class="header">AhitoApp</div>
    <WelcomePage />
  </div>
</template>

<script>
import WelcomePage from "./components/WelcomePage.vue";

export default {
  name: "App",
  components: {
    WelcomePage,
  },
};
</script>

<style>
*,
*:before,
*:after {
  margin: 0;
  padding: 0;

  -webkit-box-sizing: border-box !important;
  -moz-box-sizing: border-box !important;
  -ms-box-sizing: border-box !important;
  box-sizing: border-box !important;
}
body {
  margin: 0;
}
#app {
  font-family: Arial, Helvetica, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  position: relative;
}
.header {
  top: 0;
  left: 0;
  right: 0;
  z-index: 3;
  position: absolute;
  padding: 10px;
  background: #111;
  height: 50px;
  font-size: 24px;
  display: flex;
  align-items: center;
  justify-content: center;
  color: #fff;
  font-weight: 600;
}
</style>

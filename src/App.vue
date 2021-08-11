<template>
  <div id="app">
    <LandingPage />
  </div>
</template>

<script>
import LandingPage from "./pages/LandingPage";

export default {
  name: "App",
  components: {
    LandingPage,
  },
};
</script>

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #000;
  margin: 0;
  padding: 0;
  font-size: 14px;
}

body {
  background: #004c54;
  height: 100%;
}
</style>

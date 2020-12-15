<template>
  <Home />
</template>

<script>
import Home from "./components/Home.vue";

export default {
  name: "App",
  components: {
    Home
  }
};
</script>

<style>
* {
  box-sizing: border-box;
}

html {
  font-size: 62.5%;
}

body {
  margin: 0;
  display: flex;
  align-items: center;
  justify-content: center;
  height: 100vh;
  overflow: hidden;
  background: #111;
}
</style>

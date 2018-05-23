<template>
  <div id="app">
    <!-- <img src="./assets/logo.png"> -->
    <Time/>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";
import Time from "./components/Time";

export default {
  name: "App",
  components: {
    HelloWorld,
    Time
  }
};
</script>

<style>
@import url("https://fonts.googleapis.com/css?family=Rubik");

#app {
  height: 1920px;
  width: 1080px;
  font-family: "Rubik", sans-serif;
  color: white;
}
body {
  margin: 0;
  background-color: black;
}
</style>

<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <!-- <Icon /> -->
    <eltree />
    <Scroll />
    <Expandwithback />
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import Expandwithback from "./components/expandWithBack.vue";
import Icon from "./components/icon.vue";
import Scroll from "./components/scroll.vue";
import eltree from "./components/eltree.vue";

export default {
  name: "app",
  components: {
    HelloWorld,
    Icon,
    Scroll,
    Expandwithback,
    eltree
  },
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

<template>
  <div id="app">
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <HelloWorld msg="Welcome to Your Vue.js App"/>
    <!-- <Icon /> -->
    <!-- <eltree /> -->
    <!-- <Scroll /> -->
    <!-- <Expandwithback /> -->
    <!-- <slotCpnt>
      www.baidu.com
    </slotCpnt> -->
    <!-- <OutOfMemoryTestVue /> -->
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld.vue";
import Expandwithback from "./components/expandWithBack.vue";
import Icon from "./components/icon.vue";
import Scroll from "./components/scroll.vue";
import eltree from "./components/eltree.vue";
import slotCpnt from "./components/slotCpnt.vue";
import OutOfMemoryTestVue from './components/outOfMemoryTest.vue';

export default {
  name: "app",
  components: {
    HelloWorld,
    Icon,
    Scroll,
    Expandwithback,
    eltree,
    slotCpnt,
    OutOfMemoryTestVue
  },
};
</script>

<style scoped>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.container{
  display: grid;
  place-items: center;
  width: 200px;
  height: 200px;
}
</style>

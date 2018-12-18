
<template>
  <div id="app">
    <h1>Vue</h1>
    <hr>
    <!-- <img alt="Vue logo" src="./assets/logo.png"> -->
    <!-- <HelloWorld msg="Welcome to Your Vue.js App"/> -->
    <!-- <test-one /> -->
    <!-- <bubble-calculator/> -->
    <!-- <hello-world/> -->
    <!-- <bubble-box msg="Hi from the bubble!"/> -->
    <!-- <bubble-box msg="Hi from another bubble!"/> -->
    <test-axios></test-axios>
    <!-- <news-api></news-api> -->
  </div>
</template>

<script>
import NewsApi from "./components/NewsApi";
import TestAxios from "./components/TestAxios";
import TestOne from "./components/TestOne.vue";
import HelloWorld from "./components/HelloWorld.vue";
import BubbleBox from "./components/BubbleBox.vue";
import BubbleCalculator from "./components/BubbleCalculator.vue";

export default {
  name: "app",
  components: {
    "news-api": NewsApi,
    "test-axios": TestAxios,
    TestOne,
    BubbleCalculator,
    HelloWorld,
    BubbleBox
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

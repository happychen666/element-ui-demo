<template>
  <div id="app">
    <img src="./assets/logo.png" />
    <template v-for="(item, index) in navData">
      <hello :key="index" :index-data="index" :menu-data="item"></hello>
    </template>
  </div>
</template>

<script>
import Hello from "./components/Hello";

export default {
  name: "app",
  components: {
    Hello,
  },
  data() {
    return {
      navData: [
        {
          navTitle: {
            name: "rrr",
          },
          index: "0",
        },
        {
          navTitle: {
            name: "jj",
          },
          index: "1",
        },
        {
          navTitle: {
            name: "kkk",
          },
          index: "2",
        },
        {
          navTitle: {
            name: "lll",
          },
          index: "3",
        },
      ],
    };
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

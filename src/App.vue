<template>
  <div id="app">
    <div>
      <Current></Current>
      <Table />
    </div>
    <div></div>
  </div>
</template>

<script>
import HelloWorld from "./components/HelloWorld";
import Table from "./components/Table";
import Plaintable from "./components/Plaintable";
import Current from "./components/Current";

export default {
  name: "App",
  components: {
    Current,
  },
};
</script>
   

<style>
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center;*/
  margin-left: 100px;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png" />
    <node-tree :treeData="treeData" />
  </div>
</template>

<script>
import NodeTree from "./components/NodeTree.vue";
import treeData from "../public/static/node_modules.json";

export default {
  name: "App",
  components: {
    NodeTree,
  },
  data: function () {
    return {
      treeData,
    };
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

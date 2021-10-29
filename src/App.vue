<template>
  <div id="app">
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
  color: #2c3e50;
  margin-top: 60px;
}

li {
  list-style-type: none;
}
</style>

<template>
  <li :class="['link-node', selected ? 'link-node_selected' : '']">
    <img class="arrow-icon" src="../assets/arrow-icon.svg" alt="arrow-icon" />
    <a class="link-node__label" @click="handleOnClick">{{ node.name }}</a>
  </li>
</template>

<script>
export default {
  name: "LinkNode",
  props: {
    node: Object,
    selectedItemPath: String,
    pathToParent: Array,
  },
  data: function () {
    return {
      pathToNode: "",
    };
  },
  mounted() {
    this.pathToNode = this.pathToParent.concat([this.node.name]).join("/");
  },
  methods: {
    handleOnClick() {
      this.$emit("select-item", this.pathToNode);
    },
  },
  computed: {
    selected() {
      return this.selectedItemPath === this.pathToNode;
    },
  },
};
</script>

<style scoped>
.link-node {
  display: flex;
  align-items: center;
}
.link-node__label {
  color: rgb(204, 207, 38);
  padding: 3px;
  cursor: pointer;
}

.link-node_selected {
  background-color: #8cc6ef;
}

.link-node_selected .link-node__label {
  color: white;
}
.arrow-icon {
  width: 20px;
  height: 20px;
}
</style>

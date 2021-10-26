<template>
  <li :class="['file-node', selected ? 'file-node_selected' : '']">
    <img class="file-icon" src="../assets/file-ico.svg" alt="file-icon" />
    <span class="file-node__label" @click="handleOnClick">{{ node.name }}</span>
  </li>
</template>

<script>
export default {
  name: "FileNode",
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
.file-node {
  padding: 3px 0 3px;
  display: flex;
  align-items: center;
}
.file-node__label {
  color: green;
  cursor: pointer;
}

.file-icon {
  width: 20px;
  height: 20px;
}

.file-node_selected {
  background-color: #8cc6ef;
}

.file-node_selected .file-node__label {
  color: white;
}
</style>

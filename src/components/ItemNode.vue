<template>
  <li
    v-if="node.type === 'file'"
    :class="['file-node', selected ? 'file-node_selected' : '']"
  >
    <img class="file-icon" src="../assets/file-ico.svg" alt="file-icon" />
    <span class="file-node__label" @click="handleOnClick">{{ node.name }}</span>
  </li>
  <li
    v-else-if="node.type === 'link'"
    :class="['link-node', selected ? 'link-node_selected' : '']"
  >
    <img class="arrow-icon" src="../assets/arrow-icon.svg" alt="arrow-icon" />
    <a class="link-node__label" @click="handleOnClick">{{ node.name }}</a>
  </li>
</template>

<script>
export default {
  name: "ItemNode",
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

<template>
  <li v-if="node.type === 'directory'" class="dir">
    <div class="node-header" @click="handleChevronClick">
      <img
        :class="classObject"
        src="../assets/chevron-right.svg"
        alt="chevron-icon"
      />
      <img class="folder-icon" src="../assets/folder.svg" alt="folder-icon" />
      <span class="node-header__label">{{ node.name }}</span>
    </div>
    <ul
      v-if="node.contents && node.contents.length && rendered"
      v-show="expanded"
      class="dir__node-list"
    >
      <directory
        v-for="child in node.contents"
        :node="child"
        :key="child.name"
        @select-item="handleOnClick"
        :selectedItemPath="selectedItemPath"
        :pathToNode="pathToNode.concat([node.name])"
      />
    </ul>
  </li>
  <file-node
    v-else-if="node.type === 'file'"
    :node="node"
    :selectedItemPath="selectedItemPath"
    @select-item="handleOnClick"
    :pathToParent="pathToNode"
  ></file-node>
  <link-node
    v-else-if="node.type === 'link'"
    :node="node"
    :selectedItemPath="selectedItemPath"
    @select-item="handleOnClick"
    :pathToParent="pathToNode"
  ></link-node>
</template>


<script>
import FileNode from "./FileNode.vue";
import LinkNode from "./LinkNode.vue";

export default {
  name: "Directory",
  props: {
    node: Object,
    selectedItemPath: String,
    pathToNode: Array,
  },
  data: function () {
    return {
      rendered: false,
      expanded: false,
    };
  },
  components: {
    FileNode,
    LinkNode,
  },
  computed: {
    classObject: function () {
      return {
        "node-header__chevron": true,
        "node-header__chevron_expanded": this.expanded,
      };
    },
  },
  methods: {
    handleChevronClick() {
      this.expanded = !this.expanded;
      this.rendered = true;
    },
    handleOnClick(itemName) {
      this.$emit("select-item", itemName);
    },
  },
};
</script>

<style scoped>
.node-header {
  display: flex;
  cursor: pointer;
  margin-left: -20px;
}

.node-header__label {
  color: #7c4343;
  font-size: 18px;
}

.node-header__chevron {
  width: 20px;
  height: 20px;
}

.node-header__chevron_expanded {
  transform: rotate(90deg);
}

.folder-icon {
  width: 20px;
  height: 20px;
}
</style>

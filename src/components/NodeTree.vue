<template>
  <div class="tree">
    <div class="tree__file-path">
      {{ `Путь до выбранного элемента: ${selectedItemPath}` }}
    </div>
    <div class="tree__list">
      <ul>
        <directory
          :node="treeData"
          @select-item="handleSelectItem"
          :selectedItemPath="selectedItemPath"
          :pathToNode="[]"
        />
      </ul>
    </div>
  </div>
</template>

<script>
import Directory from "./Directory.vue";
export default {
  name: "NodeTree",
  components: { Directory },
  data: function () {
    return {
      selectedItemPath: "",
    };
  },
  props: {
    treeData: Object,
  },
  methods: {
    handleSelectItem(itemPath) {
      if (this.selectedItemPath !== itemPath) {
        this.selectedItemPath = itemPath;
      } else {
        this.selectedItemPath = "";
      }
    },
  },
};
</script>

<style scoped>
.tree__file-path {
  width: 100%;
  position: sticky;
  top: 0;
  height: 40px;
  background-color: white;
  display: flex;
  align-items: center;
  justify-content: center;
  z-index: 10;
  font-size: 24px;
  padding: 20px;
  color: #505076;
}
</style>

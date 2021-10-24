<template>
  <div class="tree">
    <ul class="tree-list">
      <directory :node="treeData" />
    </ul>
  </div>
</template>

<script>
import Directory from './Directory.vue'
export default {
  components: { Directory },
  name: 'NodeTree',
  props: {
    treeData: Object
  }
}
</script>

<style scoped>

</style>

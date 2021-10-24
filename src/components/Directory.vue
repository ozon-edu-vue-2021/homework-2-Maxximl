<template>
  <li class="node-tree">
    <span class="label">Папка </span>
    <ul v-if="node.contents && node.contents.length">
      <directory
        v-for="child in node.contents"
        :node="child"
        :key="child.name"
      />
    </ul>
  </li>
</template>

<script>
export default {
  name: "Directory",
  props: {
    node: Object,
  },
};
</script>

<style scoped>
</style>

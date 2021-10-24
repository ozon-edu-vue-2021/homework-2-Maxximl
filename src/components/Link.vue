<template>
    <li class="node-tree">
    <span class="label">{{node.name}}</span>
  </li>
</template>

<script>
export default {
  name: 'Directory',
  props: {
    node: Object
  }



  }
</script>

<style scoped>

</style>

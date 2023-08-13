<template>
  <div id="app">
    <el-tree
      :data="data"
      :props="defaultProps"
      @node-click="handleNodeClick"
      highlightCurrent
      @node-contextmenu="handleContextMenu"
    ></el-tree>
  </div>
</template>

<script>
export default {
  methods: {},

  data() {
    return {};
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>

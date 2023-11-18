<template>
  <div id="app">
    <!-- TODO: 补全 el-tree 组件的使用 -->
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
  methods: {
    // 处理节点点击事件
    handleNodeClick(data, node, vm) {
      console.log(data, node, vm);
    },
    // 处理右键点击事件
    handleContextMenu(event, data, node, vm) {
      console.log(event, data, node, vm);
    },
  },

  data() {
    return {
      // 定义树的数据源
      data: [
        {
          label: "中国",
          children: [
            {
              label: "广东",
              children: [
                {
                  label: "广州",
                },
                {
                  label: "深圳",
                },
              ],
            },
            {
              label: "江苏",
              children: [
                {
                  label: "南京",
                },
                {
                  label: "苏州",
                },
              ],
            },
          ],
        },
      ],
      // 定义树的属性
      defaultProps: {
        label: "label",
        children: "children",
      },
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped></style>

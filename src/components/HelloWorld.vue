<template>
  <div class="hello">
    <el-tree
      :data="data"
      show-checkbox
      :default-expanded-keys="expandedKeys"
      node-key="id"
      :check-strictly="true"
      ref="tree"
      highlight-current
      @check="handleCheckChange"
      :props="defaultProps"
      @node-contextmenu="handleNodeContextMenu"
    >
    </el-tree>
    {{ num }}
    <div class="buttons">
      <el-button @click="getCheckedNodes">通过 node 获取</el-button>
      <el-button @click="getCheckedKeys">通过 key 获取</el-button>
      <el-button @click="setCheckedNodes">通过 node 设置</el-button>
      <el-button @click="setCheckedKeys">通过 key 设置</el-button>
      <el-button @click="resetChecked">清空</el-button>
    </div>
    <div style="width:600px">
      <el-table
        :data="table_data"
        border
        style="width: 100%"
        @row-contextmenu="handleRowContextmenu"
      >
        <el-table-column prop="name" label="姓名" width="180">
        </el-table-column>
        <el-table-column prop="list" label="列表" width="180">
        </el-table-column>
        <el-table-column prop="data" label="数据">
          <template slot-scope="scope">
            <!-- <div class="scrollable-cell"> -->
				<el-scrollbar class="scrollable-cell">
              <!-- 最后一列的内容 -->
              {{ scope.row.data }}
            <!-- </div> -->
		</el-scrollbar>
          </template>
        </el-table-column>
      </el-table>
    </div>
  </div>
</template>

<script>
export default {
  methods: {
    // 获取选中节点
    getCheckedNodes() {
      console.log(this.$refs.tree.getCheckedNodes());
    },
    // 获取选中节点的 key
    getCheckedKeys() {
      console.log(this.$refs.tree.getCheckedKeys());
    },
    // 设置选中指定节点
    setCheckedNodes() {
      this.$refs.tree.setCheckedNodes([
        {
          id: 5,
          label: "二级 2-1",
        },
        {
          id: 9,
          label: "三级 1-1-1",
        },
      ]);
    },
    // 通过 key 设置选中节点
    setCheckedKeys() {
      this.$refs.tree.setCheckedKeys([3]);
    },
    // 清空选中
    resetChecked() {
      // this.$refs.tree.setCheckedKeys([]);
      this.$set(this.num, 0, (this.num[0] += 1));
      console.log(this.num);
    },
    // 处理勾选变化
    handleCheckChange(data, checked) {
      console.log(data, checked);
      if (this.list.length > 0) {
        console.log(this.list);
        checked.checkedNodes.forEach((el) => {
          if (el.floor == data.floor) {
            console.log(111);
          } else {
            console.log(2222);
            this.list = [data];
            this.$refs.tree.setCheckedNodes(this.list);
            // setCheckedNodes
          }
        });
      } else {
        this.list.push(data);
      }
    },
    // 处理右键菜单
    handleRowContextmenu(row, b, c) {
      console.log(row, b, c);
      let treeNode = this.findTreeNode(this.$refs.tree.root, row);
      if (treeNode) {
        console.log(this.$refs.tree.expand, treeNode);
        // this.$refs.tree.expand(treeNode, true);
        this.$refs.tree.setCurrentKey(treeNode.data.id);
        this.expandedKeys.push(treeNode.data.id);
      }
    },
    // 查找树节点
    findTreeNode(root, data) {
      console.log(root, data);
      if (root.data.id === data.id) {
        return root;
      } else if (root.childNodes) {
        for (let i = 0; i < root.childNodes.length; i++) {
          let node = this.findTreeNode(root.childNodes[i], data);
          if (node) {
            return node;
          }
        }
      }
      return null;
    },
    // 处理节点右键菜单
    handleNodeContextMenu(e, node) {
      console.log(e, node, "handleNodeContextMenu");
      this.$refs.tree.setCurrentKey(node.id);
    },
  },

  data() {
    return {
      num: [1, 2, 3, 4, 5, 6],
      list: [],
      data: [
        {
          id: 1,
          label: "一级 1",
          floor: 1,
          children: [
            {
              id: 2,
              label: "一级 2",
              floor: 1,
              children: [
                {
                  id: 5,
                  label: "二级 2-1",
                  floor: 2,
                },
                {
                  id: 6,
                  label: "二级 2-2",
                  floor: 2,
                },
              ],
            },
            {
              id: 3,
              label: "一级 3",
              floor: 1,
              children: [
                {
                  id: 7,
                  label: "二级 3-1",
                  floor: 2,
                },
                {
                  id: 8,
                  label: "二级 3-2",
                  floor: 2,
                },
              ],
            },
            {
              id: 4,
              label: "二级 1-1",
              floor: 2,
              children: [
                {
                  id: 9,
                  label: "三级 1-1-1",
                  floor: 3,
                },
                {
                  id: 10,
                  label: "三级 1-1-2",
                  floor: 3,
                },
              ],
            },
          ],
        },
      ],
      table_data: [
        {
          name: "王小虎1",
          list: "列表1",
          id: 2,
        },
        {
          name: "王小虎2",
          list: "列表2",
          id: 7,
        },
        {
          name: "王小虎3",
          list: "列表3",
          id: 8,
        },
        {
          name: "王小虎4",
          list: "列表4",
          data:
            "王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4王小虎4",
          id: 9,
        },
      ],
      defaultProps: {
        children: "children",
        label: "label",
      },
      expandedKeys: [],
    };
  },
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.scrollable-cell{
	white-space: nowrap;
}
::v-deep .el-scrollbar__bar.is-horizontal{
	height: 0;
}
</style>

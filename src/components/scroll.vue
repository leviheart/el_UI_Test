<template>
  <div>
    <!-- 下拉菜单元素分组展示 -->
    <transition name="slide">
      <div class="container" v-if="dropdownOpen">
        <div class="row" v-for="(group, index) in displayedGroups" :key="index">
          <div v-for="(item, innerIndex) in group" :key="innerIndex">
            {{ item }}
          </div>
        </div>
      </div>
    </transition>
    <!-- 下拉菜单展开/收起按钮 -->
    <button v-if="showDropdownButton" @click="toggleDropdown">
      {{ dropdownOpen ? "收起" : "展开" }}
    </button>
    <!-- 假设内容宽度小于300px时不显示滚动条，大于300px时显示横向滚动条 -->
    <div class="scrollContainer">
      <el-scrollbar :wrap-style="scrollbarWrapStyle">
        <!-- 这里放置你的内容 -->
        <div class="content">
          <!-- 内容部分 -->
          <div class="scroll1">111</div>
          <div class="scroll2">222</div>
          <div class="scroll3">333</div>
        </div>
      </el-scrollbar>
    </div>
  </div>
</template>
<style scoped>
.slide-enter-active,
.slide-leave-active {
  transition: all 2s cubic-bezier(0.55, 0, 0.1, 1);
}

.slide-enter,
.slide-leave-to {
  opacity: 0;
  transform: translateY(-20px);
}
.container {
  /* 设置flex布局 */
  display: flex;
  flex-wrap: wrap;
}
.row {
  /* 设置flex布局 */
  display: flex;
  width: 100%;
}
.row > div {
  /* 每行显示两个元素 */
  flex: 1 1 50%;
}
/* 根据内容宽度决定是否显示滚动条 */
.el-scrollbar__wrap {
  overflow-x: auto;
}

/* 隐藏滚动条 */
.el-scrollbar__wrap::-webkit-scrollbar {
  width: 0;
  height: 0;
}
.scrollContainer {
  width: 300px;
}
.content {
  display: flex;
  flex: 1;
  width: 100%;
}
.scroll1 {
  background: #000;
  min-width: 140px;
}
.scroll2 {
  background: #f00;
  min-width: 240px;
}
.scroll3 {
  background: #ff0;
  min-width: 340px;
}
</style>
<script>
// 导入外部的js文件
import a from "@/assets/test.js";
// 导入test.js文件中的多个命名导出
import { b, c } from "@/assets/test.js";

export default {
  // 定义组件的数据
  data() {
    return {
      // 存储下拉菜单的所有元素
      items: [],

      // 存储分组后的元素
      groupedItems: [],

      // 存储要显示的分组
      displayedGroups: [],

      // 标记下拉菜单是否展开
      dropdownOpen: false,

      // 根据内容宽度决定是否显示滚动条
      scrollbarWrapStyle: {
        overflowX: "auto",
        maxWidth: "300px", // 内容宽度的阈值,可根据需要调整
      },
    };
  },

  // 计算属性
  computed: {
    // 根据下拉菜单元素数量判断是否显示按钮
    showDropdownButton() {
      return this.items.length > 2;
    },
  },

  // 方法
  methods: {
    // 切换下拉菜单展开状态
    toggleDropdown() {
      // 定义局部变量
      let d = JSON.parse(JSON.stringify({ d: 4 }));
      let e = JSON.stringify({ d: 4 });
      let f = JSON.parse('{"d":4}');

      // 打印导入的变量和局部变量
      console.log(a, b, c, d, e, f);

      this.dropdownOpen = !this.dropdownOpen;

      // 展开时显示所有分组
      if (this.dropdownOpen) {
        this.displayedGroups = [...this.groupedItems];
      } else {
        // 收起时只显示第一行分组
        this.displayedGroups = this.groupedItems.slice(0, 1);
      }
    },
  },

  // 生命周期钩子 - 挂载完成
  mounted() {
    // 异步请求或其他方式获取下拉菜单的元素数据,并将数据存储在items数组中
    // 示例数据:
    this.items = ["元素1", "元素2", "元素3", "元素4", "元素5", "元素6"];

    // 分组处理数据
    this.groupedItems = this.items.reduce((result, item, index) => {
      if (index % 2 === 0) {
        result.push([item]);
      } else {
        result[Math.floor(index / 2)].push(item);
      }
      return result;
    }, []);

    console.log(this.groupedItems, "this.groupedItems");

    // 默认只显示第一行分组
    this.displayedGroups = this.groupedItems.slice(0, 1);
  },
};
</script>

// 总结: // 1. 导入外部js文件 // 2. 定义组件的数据、计算属性、方法 // 3.
在mounted钩子中获取下拉菜单数据,处理分组 // 4. methods中切换下拉菜单展开状态 //
5. 根据下拉菜单元素数量判断是否显示按钮

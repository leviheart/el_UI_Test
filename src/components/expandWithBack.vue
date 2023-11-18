<template>
  <div>
    <div class="header" @click="toggleList">点击展开/收起列表</div>
    <transition name="slide">
      <!-- 用transition包裹要动画的元素 -->
      <div class="list-container" v-if="isListOpen">
        <!-- v-for循环生成列表项 -->
        <div class="list-item" v-for="item in list" :key="item.id">
          {{ item.text }}
        </div>
      </div>
    </transition>
  </div>
</template>

<script>
export default {
  data() {
    return {
      list: [
        { id: 1, text: "Item 1" },
        { id: 2, text: "Item 2" },
        { id: 3, text: "Item 3" },
        // 添加更多列表项
        { id: 4, text: "Item 4" },
        { id: 5, text: "Item 5" },
      ],
      isListOpen: false, // 控制展开收起状态
    };
  },
  methods: {
    toggleList() {
      this.isListOpen = !this.isListOpen; // 切换展开收起状态
    },
  },
};
</script>

<style scoped>
.slide-enter-active,
.slide-leave-active {
  /* 添加渐变动画 */
  transition: all 3s cubic-bezier(0.55, 0, 0.1, 1);
}

.slide-enter,
.slide-leave-to {
  /* 设置动画起始和结束状态 */
  opacity: 0;
  transform: translateY(-10px);
}
</style>

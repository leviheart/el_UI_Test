<template>
  <div>
    <div class="header" @click="toggleList">
      点击展开/收起列表
    </div>
    <transition name="fade">
      <div class="list-container" v-if="isListOpen">
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
        // Add more items as needed
      ],
      isListOpen: false,
    };
  },
  methods: {
    toggleList() {
      this.isListOpen = !this.isListOpen;
    },
  },
};
</script>

<style>
.fade-enter-active, .fade-leave-active {
  transition: opacity 3s ease;
}
.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>

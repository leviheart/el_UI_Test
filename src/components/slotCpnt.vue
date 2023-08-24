<template>
  <a
  :href="url"
  class="nav-link"
>
  <slot></slot>
</a>
 </template>
<style scoped>
.nav-link{
  font-size: 20px;
}
</style>
<script>
export default {
  data() {
    return {
      // url: "www.baidu.com"
      url: "https://www.baidu.com/"
    };
  },
  computed: {},
  methods: {},
  mounted() {},
};
</script>

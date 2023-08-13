<template>
    <div class="hello">
        <i :class="title3.icon" class="iconFa"></i>
        <i class="el-icon-edit"></i>
    </div>
</template>

<script>
export default {
    methods: {

    },

    data() {
        return {
            title3:{ icon: "el-icon-s-order" }
        };
    }
};
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.iconFa {
    font-size: 15px;
}
</style>

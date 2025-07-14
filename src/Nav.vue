<script setup>
    defineProps(["title","subtitle","color","backgroundColor"]);
</script>

<template>
    <nav :style="{color:color, backgroundColor:backgroundColor}">
        <div>{{ title }}</div>
        <div>{{ subtitle }}</div>
    </nav>
</template>

<style scoped>
    nav{
        padding: 10px;
        /* background-color: #999; */
        margin-bottom: 20px;
        /* border: solid 1px #ddd; */
    }
</style>
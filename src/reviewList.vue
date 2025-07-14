<script setup>
    defineProps(["reviews"]);
</script>

<template>
    <div class="list" v-for="content in reviews">
        <div class="name">評論人：{{ content.name }}</div>
        <div class="message">評論內容：{{ content.message }}</div>
        <div class="star">評價:{{ content.star }}</div>
    </div>
    
</template>


<style scoped>
    .list{
        border-bottom: solid 1px #999;
        padding: 10px 0;
    }

    .name{
        font-weight: bold;
    }

</style>
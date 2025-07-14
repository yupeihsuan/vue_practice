<script setup>
    defineProps(["products"]);
</script>

<template>
    <div class="list" v-for="content in products">
        <div class="name">產品名稱：{{ content.name }}</div>
        <div class="description">產品說明：{{ content.description }}</div>
        <div class="price">單價:{{ content.price }}</div>
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
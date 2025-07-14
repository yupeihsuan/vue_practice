<script setup>

    import {onMounted,ref} from "vue"; 
    import productList from "./productList.vue";
     
    let products = ref(null);

    onMounted(async function(){
        let response = await fetch("https://cwpeng.github.io/live-records-samples/data/products.json");
        let data = await response.json();
        products.value = data;
    });
</script>

<template>

    <section class="productSection">
        <div v-if="products==null">資料載入中...</div>
        <productList v-else :products="products"></productList>
    </section>

</template>

<style scoped>
    .productSection{
        background-color: #f7f7f7;
        color:#666;
        padding: 10px;
        border: solid 1px #333;
        margin-top: 15px;
    }
</style>
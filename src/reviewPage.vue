<script setup>

    import {onMounted,ref} from "vue"; 
    import reviewList from "./reviewList.vue";
     
    let reviews = ref(null);

    onMounted(async function(){
        let response = await fetch("https://cwpeng.github.io/live-records-samples/data/reviews.json");
        let data = await response.json();
        reviews.value = data;
    });
</script>

<template>

    <section class="reviewSection">
        <div v-if="reviews==null">資料載入中...</div>
        <reviewList v-else :reviews="reviews"></reviewList>
    </section>

</template>

<style scoped>
    .reviewSection{
        background-color: #f7f7f7;
        color:#666;
        padding: 10px;
        border: solid 1px #333;
        margin-top: 15px;
    }
</style>
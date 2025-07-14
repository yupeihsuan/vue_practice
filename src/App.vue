<script setup>
    import NavComp from "./Nav.vue";
    import MainComp from "./Main.vue"
    import productPage from "./productPage.vue";
    import reviewPage from "./reviewPage.vue";
    import {onMounted,ref} from "vue";

    let subtitle = ref("副標題");
    let updateSubtitle = function(){
        subtitle.value = "Vue 的基本練習-1";
    };

    let visible = ref(true);

    let hide = function(){
        visible.value = false;
    };

    let show = function(){
        visible.value = true;
    };

    let page = ref("product");

    let change = function(clickedPage){
        page.value = clickedPage;
    }


</script>
 
<template>

    <NavComp
        title="基本導覽列"
        :subtitle = "subtitle"
        color = "#333"
        backgroundColor = "#999">
        
    </NavComp>

    
    <MainComp @update = "updateSubtitle" v-if="visible"></MainComp>

    <button @click="hide">隱藏內容</button>
    <button @click="show">重新顯示</button>


    <section class="switchSection">
        <nav>
            <span :class="page=='product'?'current':''" @click="change('product')">產品資料</span>
            <span :class="page=='review'?'current':''" @click="change('review')">評論訊息</span>
        </nav>

        <main>
            <productPage v-if="page=='product'"></productPage>
            <reviewPage v-else></reviewPage>
        </main>
    </section>

</template>

<style scoped>
    button{
        margin: 8px 10px;
    }

    .headline{
        font-size: 18px;
    }

    nav{
        font-size: 20px;
        color:#666;
    }

    nav>span{
        margin-right: 10px;
    }

    nav>span:hover{
        text-decoration: underline;
        cursor: pointer;
    }

    nav>span.current{
        font-weight: bold;
        color: #333;
    }

    .switchSection{
        margin-top: 15px;
    }

</style>

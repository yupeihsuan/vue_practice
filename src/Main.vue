<script setup>

    import {onMounted,onUpdated,onUnmounted,ref} from "vue";


    //console.log("第一個組件"); 
    let message = "<u>Hello Vue</u>";
    let name = "content";
    let checked = true;
    let score = 5;
    let data = ['A','B','C','D'];
    let data1 = {"x":3,"y":4};
    let level = ["level 1","level 2","level 3","level 4"];

    let course = [
    { name: "HTML", level: "level 1" },
    { name: "CSS", level: "level 2" },
    { name: "JavaScript", level: "level 3" },
    { name: "Vue.js", level: "level 4" }
    ];

    let state = ref({
        title:"舊的內容",
        className:"title"
    });

    let handler = function(){
        console.log("Click");
        state.value.title = "新的內容";
        state.value.className = "title1";
    };

    let mouseoverHandler = function(){
        console.log("Mouse Over");
    };

    let inputBox = ref("");
    let gender = ref(null);
    let animals = ref([]);
    let job = ref("");
    let color = ref(null);

    let clearContent = function(){
        inputBox.value = "";
        gender.value = null;
        animals.value = [];
        job.value = "";
        color.value = null;
    }

    // onMounted(function(){
    //     console.log("組件載入完成");
    // });

    // onUpdated(function(){
    //     console.log("組件更新完成");
    // });

    // onUnmounted(function(){
    //     console.log("組件卸載完成");
    // });

    let counter = ref(0);
    let timeId;

    onMounted(function(){
        timeId = window.setInterval(function(){
            counter.value+=1;
            // console.log("時間+1");
        },1000);
    }); 

    onUnmounted(function(){
        window.clearInterval(timeId);
    });

    

    
    

</script>
 
<template>
    <main>
        <button @click="$emit('update')">改變標題文字</button>
        <hr>

        <div>計時：{{ counter }} 秒</div>
        <hr>
        
        <div :class="name">操作標籤的屬性</div>
        <div :class="checked?'dark':'light'">三元運算</div>
        <hr>

        <p class="description">if else-if else 練習</p>
        <div v-if="score<60">Failed</div>
        <div v-else-if="score==100">Excellent</div>
        <div v-else>Good</div>
        <hr>

        <p class="description">for迴圈練習-1</p>
        <div v-for="n in data">Item{{ n }}</div>
        <hr>

        <!-- <div v-for="(變數1,變數2) in 陣列"> -->
        <!-- 變數1抓取陣列裡的資料，變數2表示資料位置 -->
        <p class="description">for迴圈練習-2</p>
        <div v-for="(text,index) in data">
            Index {{ index }} is {{ text }}
        </div>
        <hr>

        <p class="description">for迴圈練習-3</p>
        <div v-for="(value,key) in data1">
            物件屬性{{key}}為{{value}}
        </div>
        <hr>

        <p class="description">綜合練習</p>
        <div>
            <ul>
                <li v-for="n in level">{{ n }}</li>
            </ul>

            <ul>
                <li v-for="(item,index) in course">
                    Course {{ index+1 }} is {{ item.name }}, and its {{ item.level }}
                </li>
            </ul>
        </div>
        <hr>

        <p class="description">事件處理、響應式狀態</p>
        <div :class="state.className">{{ state.title }}</div>
        <button @click="handler" @mouseover="mouseoverHandler">按鈕</button><br>
        <a @click.prevent href="https://cs.utaipei.edu.tw/">學校網站</a>
        <hr>

        <p class="description">輸入元件</p>

        <div>請輸入你的名字： <input type="text" v-model="inputBox"></div>
        <div>Hello {{inputBox}}</div>
        <hr>



        男生 <input type="radio" value="male" v-model="gender">
        女生 <input type="radio" value="female" v-model="gender">
        <div>選擇的性別： {{gender}}</div>
        <hr>

        <input type="checkbox" value="pig" v-model="animals"> 豬
        <input type="checkbox" value="dog" v-model="animals"> 狗
        <input type="checkbox" value="cat" v-model="animals"> 貓
        <input type="checkbox" value="elephant" v-model="animals"> 大象
        <div>喜歡的動物：</div>
        <ul>
            <li v-for="i in animals">{{i}}</li>
        </ul>
        <hr>

        <select v-model="job">
            <option value="">請選擇你的職業</option>
            <option value="engineer">工程師</option>
            <option value="teacher">老師</option>
            <option value="student">學生</option>
        </select>
        <div>{{inputBox}}的職業：{{job}}</div>
        <hr>

        <select v-model="color">
            <option value="">請選擇顏色</option>
            <option value="red">紅色</option>
            <option value="green">綠色</option>
        </select>
        <div :class="color">{{inputBox}}選擇的顏色：{{color}}</div>
        <br><hr>

        <button @click="clearContent">清除所有資料</button>
    </main>
</template>

<style scoped>

    .green{
        color: green;
    }

    .red{
        color: red;
    }

    main{
        background-color: #f7f7f7;
        color:#666;
        padding: 10px;
        border: solid 1px #333;
    }

    .content:hover{
        color: blue;
    }

    .light{
        color: #fff;
        background-color: lightblue;
    }

    .dark{
        color: #fff;
        background-color: darkblue;
    }

    .description{
        background-color: #ddd;
        padding: 3px 8px;
    }

    .title{
        color: red;
        font-weight: bold;
    }

    .title1{
        color: blue;
        font-size: 18px;
    }
</style>
<script setup>
import HelloWorld from './components/HelloWorld.vue'
import TheWelcome from './components/TheWelcome.vue'
import {ref} from 'vue'

const questionList = ref([
    {
      status: 'pending',
      imgSrc: 'https://lh3.googleusercontent.com/proxy/7v4jrhphB5j_n7A9AAxQPk5gdVp-kawPq2lzWV_CuZqJNVIAOkdMSPHJF5Na22xmkrGt9jU4chs1va8-xRf4qDwgtg99B5f4d_ER'
    },
    {
      status: 'pending',
      imgSrc: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTtvkIeHNGKmOJa4u8D91rJm2qCCU_y49kOr1zkxpU0sQ&s'
    },
    {
      status: 'pending',
      imgSrc: 'https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcS2eafsWmwN3TdoWbpUsb-2xtE2jl_qcTSYBVaMdumt6g&s'
    },
    {
      status: 'pending',
      imgSrc: 'https://lh3.googleusercontent.com/proxy/7v4jrhphB5j_n7A9AAxQPk5gdVp-kawPq2lzWV_CuZqJNVIAOkdMSPHJF5Na22xmkrGt9jU4chs1va8-xRf4qDwgtg99B5f4d_ER'
    },
    {
      status: 'pending',
      imgSrc: 'https://lh3.googleusercontent.com/proxy/7v4jrhphB5j_n7A9AAxQPk5gdVp-kawPq2lzWV_CuZqJNVIAOkdMSPHJF5Na22xmkrGt9jU4chs1va8-xRf4qDwgtg99B5f4d_ER'
    },
    {
      status: 'pending',
      imgSrc: 'https://lh3.googleusercontent.com/proxy/7v4jrhphB5j_n7A9AAxQPk5gdVp-kawPq2lzWV_CuZqJNVIAOkdMSPHJF5Na22xmkrGt9jU4chs1va8-xRf4qDwgtg99B5f4d_ER'
    },
    {
      status: 'pending',
      imgSrc: 'https://lh3.googleusercontent.com/proxy/7v4jrhphB5j_n7A9AAxQPk5gdVp-kawPq2lzWV_CuZqJNVIAOkdMSPHJF5Na22xmkrGt9jU4chs1va8-xRf4qDwgtg99B5f4d_ER'
    },
    {
      status: 'pending',
      imgSrc: 'https://lh3.googleusercontent.com/proxy/7v4jrhphB5j_n7A9AAxQPk5gdVp-kawPq2lzWV_CuZqJNVIAOkdMSPHJF5Na22xmkrGt9jU4chs1va8-xRf4qDwgtg99B5f4d_ER'
    },
    {
      status: 'pending',
      imgSrc: 'https://lh3.googleusercontent.com/proxy/7v4jrhphB5j_n7A9AAxQPk5gdVp-kawPq2lzWV_CuZqJNVIAOkdMSPHJF5Na22xmkrGt9jU4chs1va8-xRf4qDwgtg99B5f4d_ER'
    },
    {
      status: 'pending',
      imgSrc: 'https://lh3.googleusercontent.com/proxy/7v4jrhphB5j_n7A9AAxQPk5gdVp-kawPq2lzWV_CuZqJNVIAOkdMSPHJF5Na22xmkrGt9jU4chs1va8-xRf4qDwgtg99B5f4d_ER'
    },
    {
      status: 'pending',
      imgSrc: 'https://lh3.googleusercontent.com/proxy/7v4jrhphB5j_n7A9AAxQPk5gdVp-kawPq2lzWV_CuZqJNVIAOkdMSPHJF5Na22xmkrGt9jU4chs1va8-xRf4qDwgtg99B5f4d_ER'
    },
    {
      status: 'pending',
      imgSrc: 'https://lh3.googleusercontent.com/proxy/7v4jrhphB5j_n7A9AAxQPk5gdVp-kawPq2lzWV_CuZqJNVIAOkdMSPHJF5Na22xmkrGt9jU4chs1va8-xRf4qDwgtg99B5f4d_ER'
    },
  ]
)
const questionCurrent = ref(0)


const handleTrue = ()=> {
  console.log(questionList.value[questionCurrent.value].status);
  questionList.value[questionCurrent.value].status = 'true'
}
const handleFalse = ()=> {
  questionList.value[questionCurrent.value].status = 'false'
}
const getClass = (status,index) => {
  
  if(status == 'true') {
    return 'transparent'
  }
  if(status == 'false') {
    return 'disable'
  }
  if(questionCurrent.value == index) {
    return 'active'
  } 
}
const handleClickQuestion = (index,event) => {
  questionCurrent.value=Number(index)

}
</script>

<template>
  <div class="container">
    <div class="content-left">
      <div v-for="(question,index) in questionList" class="question-btn" :id="index" @click="(event)=>handleClickQuestion(index,event)" :class="getClass(question.status,index)">
        <div >{{ index+1 }}</div>
      </div>
    </div>
    <div class="content-right">
      <template  v-for="(question,index) in questionList">
        <div v-if="questionCurrent == index" class="img-question">
          <img  :src="question.imgSrc" alt="" srcset="">
        </div>
      </template>
      <div class="btn-wrap">
        <button class="btn-true" @click="handleTrue">Dung</button>
        <button class="btn-false"  @click="handleFalse">Sai</button>
      </div>
    </div>
  </div>
</template>
<style scoped>
:target {
  background-color: red;
}

.container {
  display: flex;
  width: 100%;
  height: 100vh;
  gap: 32px
}

.content-left {
  width: 80%;
  height: 100%;
  background-image: url('https://lh3.googleusercontent.com/proxy/7v4jrhphB5j_n7A9AAxQPk5gdVp-kawPq2lzWV_CuZqJNVIAOkdMSPHJF5Na22xmkrGt9jU4chs1va8-xRf4qDwgtg99B5f4d_ER');
  background-repeat: no-repeat;
  background-size: contain;
  background-position: center;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(3, 1fr);
  transition: all .5s ease;
}
/* .content-left:hover {
  width: 80%;
}
.content-right {
  width: 20%;
  transition: all .5s ease;
}
.content-right:hover {
  width: 160%;
} */

.question-btn {
  display: flex;
  justify-content: center;
  align-items: center;
}

.question-btn {
  background-color: wheat;
  border: 1px solid black;
  transition: all .3s ease;
}
.question-btn:hover {
  cursor: pointer;
  box-shadow: inset 0 0 10px;
}
.question-btn.active {
  box-shadow: inset 0 0 10px;
}
.question-btn.transparent {
  opacity: 0;
}
.img-question {
  width: 100%;
  margin-bottom: 24px;
}
img {
  width: 100%;
  height: 100%;
  object-fit: cover;
}
.question-btn.disable {
  pointer-events: none;
  background-color: #888;
}
.btn-wrap {
  display: flex;
  gap: 12px;

}
button:hover {
  cursor: pointer;
}
.btn-true {
  background-color: #04AA6D; 
  border: none;
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 200px;
  height: 68px;
  font-size: 32px;
}
.btn-false {
  background-color: #f44336; 
  border: none;
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 200px;
  height: 68px;
  font-size: 32px;
}
</style>

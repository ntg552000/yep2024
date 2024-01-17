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
const questionCurrent = ref()

const handleAnswer = (answer) => {
  if(answer) {
    questionList.value[questionCurrent.value].status = 'true'
  } else {
    questionList.value[questionCurrent.value].status = 'false' 
  }
  isOpenModal.value = false
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
const isOpenModal = ref(false)

const handleClickQuestion = (index,event) => {
  isOpenModal.value = true
  questionCurrent.value=Number(index)

}
</script>

<template>
    <div class="container">
      <img class="background" src="" alt="" srcset="">
      <h1>Year end party 2024</h1>
      <div class="content-left">
        <div v-for="(question,index) in questionList" class="question-btn" :id="index" @click="(event)=>handleClickQuestion(index,event)" :class="getClass(question.status,index)">
          <div >{{ index+1 }}</div>
        </div>
      </div>
      <div class="content-right" v-show="isOpenModal">
        <div class="overlay" @click="isOpenModal =!isOpenModal"></div>
        <div class="container-main">
          <template  v-for="(question,index) in questionList">
            <div v-if="questionCurrent == index" class="img-question">
              <img  :src="question.imgSrc" alt="" srcset="">
            </div>
          </template>
          <div class="btn-wrap">
            <button class="btn-true" @click="handleAnswer(true)">Dung</button>
            <button class="btn-false"  @click="handleAnswer(false)">Sai</button>
          </div>
        </div>
      </div>
    </div>
</template>
<style scoped>
.container {
  width: 100%;
  height: 100vh;
  position: relative;
  padding-top: 24px;
}
h1 {
  text-align: center;
  font-size: 50px;
}

.content-right {
  position: fixed;
  inset: 0;
}
.overlay {
  background: rgba(0,0,0,.6);
  position: absolute;
  inset: 0;
  z-index: 1;
}
.background {
  position: absolute;
  left: 0px;
  top: 0px;
  z-index: -1;
  width: 100%;
  height: 100%;
  -webkit-filter: blur(5px); /* Safari 6.0 - 9.0 */
  filter: blur(2px);
  background-image: url('https://gomsuhcm.com/wp-content/uploads/2023/11/Hinh-anh-Background-Tet-Nguyen-Dan-dep-3.jpg');
  background-repeat: no-repeat;
  background-size: cover;
  opacity: .8;

}
.container-main {
  width: 60%;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%,-50%);
  z-index: 2;
}

.content-left {
  width: 80%;
  background-image: url('https://lh3.googleusercontent.com/proxy/7v4jrhphB5j_n7A9AAxQPk5gdVp-kawPq2lzWV_CuZqJNVIAOkdMSPHJF5Na22xmkrGt9jU4chs1va8-xRf4qDwgtg99B5f4d_ER');
  background-repeat: no-repeat;
  background-size: contain;
  background-position: center;
  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(3, 1fr);
  transition: all .5s ease;
  min-height: 800px;
  max-width: 1410px;
  position: absolute;
  top: 55%;
  left: 50%;
  transform: translate(-50%,-50%);
  margin: 0 auto;
  box-shadow: rgba(0, 0, 0, 0.25) 0px 54px 55px, rgba(0, 0, 0, 0.12) 0px -12px 30px, rgba(0, 0, 0, 0.12) 0px 4px 6px, rgba(0, 0, 0, 0.17) 0px 12px 13px, rgba(0, 0, 0, 0.09) 0px -3px 5px;
}

.question-btn {
  display: flex;
  justify-content: center;
  align-items: center;
}

.question-btn {
  background-color: #fff;
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
  pointer-events: none;
}
.img-question {
  width: 100%;
  margin-bottom: 24px;
  border: 2px solid #000;
  border-radius: 50px;
  overflow: hidden;
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
  justify-content: center;
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
  border-radius: 10px;
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
  border-radius: 10px;

}
</style>

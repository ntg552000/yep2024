<script setup>
import HelloWorld from "./components/HelloWorld.vue";
import TheWelcome from "./components/TheWelcome.vue";
import { ref } from "vue";

const questionList = ref([
{
    status: "pending",
    imgSrc:
      "https://github.com/ntg552000/image-yep/blob/main/mini1.jpg?raw=true",
  },
  {
    status: "pending",
    imgSrc:
      "https://github.com/ntg552000/image-yep/blob/main/mini2.jpg?raw=true",
  },
  {
    status: "pending",
    imgSrc:
      "https://github.com/ntg552000/image-yep/blob/main/mini3.jpg?raw=true",
  },
  {
    status: "pending",
    imgSrc:
      "https://github.com/ntg552000/image-yep/blob/main/mini4.jpg?raw=true",
  },
  {
    status: "pending",
    imgSrc:
      "https://github.com/ntg552000/image-yep/blob/main/mini5.jpg?raw=true",
  },
  {
    status: "pending",
    imgSrc:
      "https://github.com/ntg552000/image-yep/blob/main/mini6.jpg?raw=true",
  },
  {
    status: "pending",
    imgSrc:
      "https://github.com/ntg552000/image-yep/blob/main/mini10.png?raw=true",
  },
  {
    status: "pending",
    imgSrc:
      "https://github.com/ntg552000/image-yep/blob/main/mini8.JPG?raw=true",
  },
  // {
  //   status: 'pending',
  //   imgSrc: 'https://lh3.googleusercontent.com/proxy/7v4jrhphB5j_n7A9AAxQPk5gdVp-kawPq2lzWV_CuZqJNVIAOkdMSPHJF5Na22xmkrGt9jU4chs1va8-xRf4qDwgtg99B5f4d_ER'
  // },
  // {
  //   status: 'pending',
  //   imgSrc: 'https://lh3.googleusercontent.com/proxy/7v4jrhphB5j_n7A9AAxQPk5gdVp-kawPq2lzWV_CuZqJNVIAOkdMSPHJF5Na22xmkrGt9jU4chs1va8-xRf4qDwgtg99B5f4d_ER'
  // },
  // {
  //   status: 'pending',
  //   imgSrc: 'https://lh3.googleusercontent.com/proxy/7v4jrhphB5j_n7A9AAxQPk5gdVp-kawPq2lzWV_CuZqJNVIAOkdMSPHJF5Na22xmkrGt9jU4chs1va8-xRf4qDwgtg99B5f4d_ER'
  // },
  // {
  //   status: 'pending',
  //   imgSrc: 'https://lh3.googleusercontent.com/proxy/7v4jrhphB5j_n7A9AAxQPk5gdVp-kawPq2lzWV_CuZqJNVIAOkdMSPHJF5Na22xmkrGt9jU4chs1va8-xRf4qDwgtg99B5f4d_ER'
  // },
]);
const questionCurrent = ref();

const handleAnswer = (answer) => {
  if (answer) {
    questionList.value[questionCurrent.value].status = "true";
  } else {
    questionList.value[questionCurrent.value].status = "false";
  }
  isOpenModal.value = false;
};

const showAll = () => {
  questionList.value = questionList.value.map((item) => ({
    ...item,
    status: "true",
  }));
};

const getClass = (status, index) => {
  if (status == "true") {
    return "transparent";
  }
  if (status == "false") {
    return "disable";
  }
  if (questionCurrent.value == index) {
    return "active";
  }
};
const isOpenModal = ref(false);

const handleClickQuestion = (index, event) => {
  isOpenModal.value = true;
  questionCurrent.value = Number(index);
};
</script>

<template>
  <div class="container background">
    <!-- <div class="background">
      </div> -->
    <div class="content-left">
      <!-- <img src="https://lh3.googleusercontent.com/proxy/7v4jrhphB5…MSPHJF5Na22xmkrGt9jU4chs1va8-xRf4qDwgtg99B5f4d_ER" /> -->
      <div
        v-for="(question, index) in questionList"
        class="question-btn"
        :id="index"
        @click="(event) => handleClickQuestion(index, event)"
        :class="getClass(question.status, index)"
      >
        <div>{{ index + 1 }}</div>
      </div>
    </div>

    <div class="content-right" v-show="isOpenModal">
      <div class="overlay" @click="isOpenModal = !isOpenModal"></div>
      <div class="container-main">
        <template v-for="(question, index) in questionList">
          <div v-show="questionCurrent == index" class="img-question">
            <img :src="question.imgSrc" alt="" srcset="" loading="lazy" />
          </div>
        </template>
        <div class="btn-wrap">
          <button class="btn-true" @click="handleAnswer(true)">Đúng</button>
          <button class="btn-false" @click="handleAnswer(false)">Sai</button>
        </div>
      </div>
    </div>

    <button class="btn-ans" @click="showAll">Show</button>
  </div>
</template>
<style scoped>
div {
  box-sizing: border-box;
}
.container {
  width: 100%;
  height: 100vh;
  max-height: 100%;
  /* min-width: 200px; */
  /* padding-top: 24px; */
}
h1 {
  text-align: center;
  font-size: 50px;
}

.content-right {
  position: fixed;
  inset: 0;
  z-index: 999;
}
.overlay {
  background: rgba(0, 0, 0, 0.6);
  position: absolute;
  inset: 0;
  z-index: 1;
}
.background {
  position: absolute;
  left: 0;
  top: 0;
  right: 0;
  bottom: 0;
  z-index: -1;
  background-image: url("./image/Minigame.png");
  background-repeat: no-repeat;
  background-size: contain;
  background-size: 100% 100%;
}
.container-main {
  width: 60%;
  position: absolute;
  top: 50%;
  left: 50%;
  transform: translate(-50%, -50%);
  z-index: 2;
  padding: 50px;
}

.content-left {
  position: absolute;

  background-image: url("./image/mini7.jpg");
  background-repeat: no-repeat;
  background-size: contain;
  transition: all 0.5s ease;
  box-shadow: rgba(0, 0, 0, 0.25) 0px 54px 55px,
    rgba(0, 0, 0, 0.12) 0px -12px 30px, rgba(0, 0, 0, 0.12) 0px 4px 6px,
    rgba(0, 0, 0, 0.17) 0px 12px 13px, rgba(0, 0, 0, 0.09) 0px -3px 5px;
  left: 23.1%;
  right: 25.2%;
  top: 25.0%;
  bottom: 10%;
  background-size: 100% 100%;

  display: grid;
  grid-template-columns: repeat(4, 1fr);
  grid-template-rows: repeat(2, 1fr);
  overflow: hidden;
  border-left: 2px solid rgb(0, 0, 0);
  border-top: 2px solid rgb(0, 0, 0);
}

.question-btn {
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
  align-items: center;
  background-color: #eba351;
  transition: all 0.3s ease;
  border-right: 2px solid rgb(0, 0, 0);
  border-bottom: 2px solid rgb(0, 0, 0);
  font-family: "Cursive", "Lucida Handwriting", monospace;
  font-size: 40px;
  color: #240707;
}
.question-btn:hover {
  cursor: pointer;
  box-shadow: inset 0 0 20px;
}
.question-btn.active {
  /* box-shadow: inset 0 0 10px; */
}
.question-btn.transparent {
  opacity: 0;
  pointer-events: none;
}
.img-question {
  width: 100%;
  margin-bottom: 24px;
  /* border-radius: 50px; */
  overflow: hidden;
  border: 8px solid rgb(233, 192, 184);
  padding: 8px;
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
  background-color: #df7f25;
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
  background-color: rgb(204, 65, 65);
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

.btn-ans {
  position: absolute;
  bottom: 10px;
  left: 50%;
  transform: translateX(-50%);
  background-color: rgb(216, 148, 21);
  border: none;
  color: white;
  display: flex;
  justify-content: center;
  align-items: center;
  width: 180px;
  height: 55px;
  font-size: 32px;
  border-radius: 10px;
}

body {
  overflow: hidden;
}
</style>

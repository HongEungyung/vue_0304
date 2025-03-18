<script setup>
import { ref } from "vue";
// 1. 버튼 클릭 이벤트
const count = ref(0);
// 2. 입력 이벤트
const message = ref(""); // 입력된 메시지를 저장하는 변수
// 3. 마우스 오버 이벤트
const hover = ref(false);
// 4. 키보드 이벤트
const newMessage = ref(""); // 키보드로 입력된 메시지
const messages = ref([]); // 추가된 메시지를 저장하는 배열
// li가 쌓이려면 []배열 안에 넣어줘야 함.
const addMessage = () => {
  if (newMessage.value) {
    messages.value.push(newMessage.value);
    newMessage.value = ""; // enter 후 입력창을 리셋(빈배열) 시켜 줌
  }
};
// 5. 폼 제출 이벤트
const username = ref("");
const saveName = ref("");
// 폼 제출 기능
const submitForm = () => {
  saveName.value = username.value; // saveName 에 username 값을 할당하겠다
};
// 6. 더블 클릭 이벤트
const color = ref("lightgray");
const toggleColor = () => {
  color.value = color.value === "lightgray" ? "lightblue" : "lightgray";
};
// 7. 마우스 위치 추적
const x = ref(0);
const y = ref(0);
// 마우스 위치 업데이트 함수
const updatePosition = (event) => {
  // event 는 원래 있는 애
  x.value = event.clientX;
  y.value = event.clientY;
};
// 8. 체크 박스
const checked = ref(false);
// 9. 컨텍스트 메뉴 (우클릭 메뉴)
const menuVisible = ref(false)
const menuX = ref(0)
const menuY = ref(0)
const showMenu = (event)=>{
    menuVisible.value = true
    menuX.value = event.clientX
    menuY.value = event.clientY
}
const selectOption = (option)=>{
// console.log(option);
alert(`${option} 선택됨`)
menuVisible.value = false
}
</script>

<template>
  <div class="container">
    <h1>vue event</h1>

    <!-- 1. 버튼 클릭 이벤트 -->
    <h3>1. 버튼 클릭 이벤트</h3>
    <button @click="count++">클릭 {{ count }} 번</button>

    <!-- 2. 입력 이벤트 -->
    <h3>2. 입력 이벤트</h3>
    <input type="text" placeholder="입력하세요." v-model="message" />
    <p>입력값 : {{ message }}</p>

    <!-- 3. 마우스 오버 이벤트 -->
    <h3>3. 마우스 오버 이벤트</h3>
    <button @mouseover="hover = true" @mouseleave="hover = false" :style="{ backgroundColor: hover ? 'blue' : '#fff', color: hover ? '#fff' : 'red' }">마우스를 올려보세요</button>

    <!-- 4. 키보드 이벤트 -->
    <h3>4. 키보드 이벤트 (enter 후 추가되기 / 입력값 계속 추가하기)</h3>
    <input type="text" v-model="newMessage" @keyup.enter="addMessage" placeholder="enter 후 입력값 출력" />
    <ul>
      <li v-for="(msg, index) in messages" :key="index">{{ msg }}</li>
    </ul>

    <!-- 5. 폼 제출 -->
    <h3>5. 폼 제출</h3>
    <!-- 폼 제출하면 username 값을 saveName 에 저장하고 경고창을 띄움 -->
    <form @submit.prevent="submitForm">
      <input type="text" v-model="username" placeholder="이름 입력" />
      <button type="submit" class="form5-btn">제출</button>
    </form>
    <p>입력된 이름 : {{ saveName }}</p>

    <!-- 6. 더블 클릭 이벤트 -->
    <h3>6. 더블클릭 이벤트</h3>
    <div class="box" :style="{ backgroundColor: color }" @dblclick="toggleColor">더블클릭하세요!</div>

    <!-- 7. 마우스 위치 추적 -->
    <h3>7. 마우스 위치 추적</h3>
    <div @mousemove="updatePosition" class="tracker">X : {{ x }} , Y {{ y }}</div>

    <!-- 8. 체크박스 -->
    <h3>8. 체크 박스</h3>
    <label>
      <input type="checkbox" v-model="checked" />
      동의합니다.
    </label>
    <p>{{ checked ? "동의하셨습니다." : "동의가 필요합니다." }}</p>

    <!-- 9. 컨텍스트 메뉴 (우클릭 메뉴) -->
    <h3>9. 컨텍스트 메뉴 (우클릭 메뉴)</h3>
    <div @contextmenu.prevent="showMenu($event)" class="tracker">우클릭하세요!</div>
    <ul v-if="menuVisible" :style="{top: `${menuY}px` , left: `${menuX}px`}" class="context-menu">
    <!-- top left 어디가 X축 Y축인지 잘 보기 -->
      <li @click="selectOption('옵션 1')">옵션 1</li>
      <li @click="selectOption('옵션 2')">옵션 2</li>
    </ul>
  </div>
</template>

<style scoped>
h1{
  text-align: center;
  margin-bottom: 20px;
}
h3{
  margin-top: 30px;
  margin-bottom: 10px;
}
/* 5. 폼 제출 */
.form5-btn{
  margin-left: 10px;
}
/* 6. 더블클릭 이벤트 */
.box {
    position: relative;
  width: 200px;
  height: 100px;
  border: 1px solid #333;
  display: flex;
  justify-content: center;
  align-items: center;
  cursor: pointer;
}
/* 7. 마우스 위치 추적 */
.tracker {
  width: 100%;
  height: 200px;
  border: 1px solid black;
  display: flex;
  justify-content: center;
  align-items: center;
}
/* 9. 컨텍스트 메뉴 (우클릭 메뉴) */
.context-menu {
  position: fixed;
  background-color: #fff;
  border: 1px solid #ccc;
  list-style: none;
  padding: 5px;
}
.context-menu li {
  padding: 5px;
  cursor: pointer;
}
.context-menu li:hover {
  background-color: antiquewhite;
}
</style>

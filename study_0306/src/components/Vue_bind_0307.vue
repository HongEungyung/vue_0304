<script setup>
import Vue_for_03072 from "./Vue_for_0307-2.vue";
import { ref } from "vue";
const imageUrl = ref("https://vuejs.org/images/logo.png");
const link = ref("https://www.naver.com/");
// 이벤트 바인딩
const count = ref(0);
const increase = () => {
  count.value++;
  // ref 라서 그냥 count 가 아니라 count.value 로 접근해야함.
};
const decrease = () => {
  count.value--;
};
// 양방향 바인딩
const message = ref("");
const items = ref(["사과", "바나나", "딸기"]);
</script>
<template>
  <div class="container">
    <h1>v-bind (import Vue_bind_0307)</h1>
    <h2>1. url , link 연결</h2>
    <img :src="imageUrl" alt="URL이미지_로고" />
    <a :href="link" target="_blank">네이버 이동</a>
    <hr />

    <!-- 이벤트 바인딩 -->
    <h2>2. 이벤트 바인딩</h2>
    <button @click="increase">+1씩 증가</button>
    <span>{{ count }}</span>
    <button @click="decrease">-1씩 감소</button>
    <hr />

    <!-- 양방향 바인딩 -->
    <h2>3. 양방향 바인딩</h2>
    <input v-model="message" />
    <p>입력한 내용 : {{ message }}</p>
    <hr />

    <!-- 반복 랜더링 v-for -->
    <h2>4. 반복 랜더링 v-for (Preview)</h2>
    <ul>
      <li v-for="(item, index) in items" :key="index">
        {{ index + 1 }}. {{ item }}
      </li>
    </ul>

    <!-- v-for -->
    <Vue_for_03072 />
  </div>
</template>
<style scoped>

img {
  width: 50px;
}
</style>

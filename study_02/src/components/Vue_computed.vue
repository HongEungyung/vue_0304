<script setup>
import { ref, computed } from "vue";
// 사용자가 입력한 검색어를 저장하는 변수
const search = ref("");
const items = ["아이폰", "갤럭시", "맥북"];
// 사용자가 입력한 검색어(search.value)가 포함된 includes(있는지 없는지 확인) 상품만 보여줌
const filterdItems = computed(() => {
  return items.filter((item) => item.includes(search.value));
});
// 상품 리스트 표시
const products = ["🚗아이폰", "🚓갤럭시", "🚕맥북"];
</script>
<template>
  <h2>검색기능</h2>
  <!-- 사용자가 입력한 검색어를 search 변수에 자동으로 반영 -->
  <!-- v-model = 입력값과 반응형 상태(양방향 데이터)를 자동 동기화 -->
  <input v-model="search" placeholder="상품검색" />
  <ul>
    <!-- v-for 반복문 사용해서 filterdItems 배열을 돌면서 li 태그로 상품표시 -->
    <li v-for="item in filterdItems" :key="item">{{ item }}</li>
  </ul>
  <hr />
  <h2>상품리스트 출력</h2>
  <ul>
    <li v-for="product in products" :key="product">{{ product }}</li>
  </ul>
</template>
<style scoped></style>

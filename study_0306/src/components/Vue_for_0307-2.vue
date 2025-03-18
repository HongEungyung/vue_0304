<script setup>
import Vue_forList3 from "./Vue_forList-3.vue";
import { ref } from "vue";
const products = ref(["노트북", "스마트폰", "태블릿"]);
const fruits = ref(["사과", "바나나", "포도"]);
// forList 예제 표시
const showfor =ref(false) 
</script>
<template>
  <div class="container">
    <h1>v-for (import Vue_for_03072)</h1>
    <ul>
      <li v-for="(product, index) in products" :key="product">
        {{ index + 1 }}. {{ product }}
      </li>
    </ul>
    <ul>
      <li v-for="(fruit, index) in fruits" :key="fruit">
        {{ index + 1 }}. {{ fruit }}
      </li>
    </ul>
    <hr />

    <div class="forList">
      <h2>v-for_ex</h2>
      <button @click="showfor = !showfor">
        {{ showfor ? "닫기" : "v-for 리스트 보기" }}
      </button>
      <!-- forList.vue 표시 여부 -->
      <Vue_forList3 v-if="showfor"/>
    </div>
  </div>
</template>
<style scoped>

</style>

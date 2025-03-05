<script setup>
import { ref } from "vue";
const show = ref(false)
const show2 = ref(false)
const isVisible = ref(false)
</script>

<template>
    <button @click="show = !show">상세설명 보기</button>
    <p v-if="show">이 상품은 정말 좋아요! 🚗</p><br>
    <button @click="show2 = !show2">추가옵션 선택하기</button>
    <p v-if="show2">red</p>
    <p v-if="show2">black</p>
    <p v-if="show2">white</p><br>

    <!-- 설명 숨기기 삼항연산자 -->
    <button @click="isVisible = !isVisible">
    {{ isVisible ? "설명 숨기기" :"설명 보기" }}
    </button>
    <p v-show="isVisible">이 제품은 품질이 뛰어나고 인기가 많아요! 🥰</p>
    <p v-show="!isVisible">이 제품은...</p>
</template>

<style scoped>

</style>
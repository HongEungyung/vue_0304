<script setup>
import { reactive, ref, computed } from "vue";
// ref로 count 상태 관리
const count = ref(0);
const increase = () => {
  count.value++;
};
// reactive 로 user 객체 관리
const user = reactive({
  name: "홍길동",
});
const toggleName = () => {
  user.name = user.name === "홍길동" ? "스폰지밥" : "홍길동";
};
// computed 로 count 값을 두배로 계산
const doubleCount = computed(() => count.value * 2);
// 오류를 최소화하기 위해서 계산할 땐 computed 써주는 게 좋음

// computed 연습
const price = ref(150);
const quantity = ref(1);
const totalPrice = computed(() => price.value * quantity.value);
</script>
<template>
  <div class="practice">
    <!-- ref로 count 상태 관리 -->
    <h1>1. Ex</h1>
    <p>Count : {{ count }}</p>
    <button @click="increase">+증가</button>
    <!-- reactive 로 user 객체 관리 -->
    <p>User Name : {{ user.name }}</p>
    <button @click="toggleName">Toggle Name</button>
    <!-- computed 로 count 값을 두배로 계산 -->
    <button>Double Count : {{ doubleCount }}</button>
    <hr />

    <!-- computed 연습 -->
    <h2>computed로 계산하기 연습</h2>
    <div class="computed">
      <div class="ex_01">
        <p>가격 : {{ price }}원</p>
        <p>수량 : {{ quantity }}개</p>
        <p>총 가격 : {{ totalPrice }}원</p>
      </div>
      <div class="ex_02">
        <P> 가격 : {{ price }}원 </P>
        <button @click="price += 10">가격 +10원</button>
        <button @click="price -= 10">가격 -10원</button>
        <hr />
        <p>수량 : {{ quantity }}개</p>
        <button @click="quantity += 1">수량 +1</button>
        <button @click="quantity -= 1" :disabled="quantity <= 1">수량 -1</button>
        <hr />
        <p>총 가격 : {{ totalPrice }}원</p>
      </div>
    </div>
  </div>
</template>
<style scoped>
.practice{
  margin-top: 50px;
}
.computed {
  width: 1000px;
  display: flex;
  gap: 20px;
}
.computed div {
  flex: 1;
  background-color: antiquewhite;
}
</style>

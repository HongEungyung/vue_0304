<script setup>
import { ref } from "vue";
import Form_0317 from "./components/Form_0317.vue";
import Reservation_0317 from "./components/Reservation_0317.vue";
import OnMounted_0318 from "./components/OnMounted_0318.vue";
const currentPage = ref("");
console.log(currentPage); // 여기선 아무것도 안 담김

const showPage = (page) => {
  // alert("클릭")
  // console.log(page);
  // 폼예제 버튼 클릭하면 콘솔에 Form_0317 뜨고
  // 예약신청 버튼 클릭하면 콘솔에 Reservation_0317 뜸
  currentPage.value = page;
  console.log(currentPage.value); // 여기서야 해당 페이지가 담김
};
</script>

<template>
  <div>
    <div class="btns">
      <button @click="showPage('Form_0317')">폼예제</button>
      <button @click="showPage('Reservation_0317')">예약신청</button>
      <button @click="showPage('OnMounted_0318')">onMounted()</button>
    </div>
    <Form_0317 v-if="currentPage === 'Form_0317'" />
    <Reservation_0317 v-if="currentPage === 'Reservation_0317'" />
    <OnMounted_0318 v-if="currentPage === 'OnMounted_0318'" />
  </div>
</template>

<style scoped>
.btns{
    width: 50%;
    display: flex;
    margin: 50px auto;
}
button {
  margin: 10px;
}
</style>

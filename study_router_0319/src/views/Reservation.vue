<script setup>
import { computed, reactive, ref } from "vue";
const isReservable = ref(false);
const selectedDate = ref("");
const selectDate = (event) => {
  selectedDate.value = event.target.value;
  isReservable.value = !!selectedDate.value; // 이중부정연산자 : 값을 반드시 불리언으로 변환하는 역할
};
// reactive
const newReservation = ref("");
const reservations = reactive([]); // 예약 리스트
const addReservation = () => {
  if (newReservation.value.trim() && selectedDate.value) {
    // 이름과 날짜가 모두 있어야 예약이 추가되게 하는 if절
    reservations.push({
      id: Date.now(), // 알아서 고유한 숫자 생성해줌
      name: newReservation.value,
      date: selectedDate.value,
    });
  }
};
console.log(reservations);
// 예약 건수 표시
const totalReservations = computed(()=>{
  return reservations.length  // return 쓰기 싫으면 { }객체 지워도 됨
})
</script>
<template>
  <div>
    <h2>예약하기</h2>
    <label>예약 날짜 선택 : </label>
    <input type="date" @input="selectDate" />
    <button @click="addReservation">예약 추가</button>
    <!-- 날짜가 선택되었을 때만 출력하기 -->
    <p v-if="selectedDate">{{ selectedDate }}</p>
    <!-- 만약에 selectedDate 가 있으면 -->
  </div>
  
  <!-- 예약 목록 관리 -->
  <div>
    <input v-model="newReservation" placeholder="이름을 입력하세요." />
    <button @click="addReservation" :disabled="!newReservation.trim() || !selectedDate">예약 추가</button>
    <ul>
      <li v-for="reservation in reservations" :key="reservation.id">{{ reservation.name }} ( 예약 날짜 : {{ reservation.date }} )</li>
    </ul>
  </div>
    <!-- 예약 건수 표시 -->
    <div>
    <p>총 예약 건수 : {{ totalReservations }}</p>
    </div>
</template>
<style scoped></style>

<script setup>
import { ref, computed, reactive } from "vue";
// 1. 예약 카운트 증가 및 두배 표시 기능
const reservation = ref(0);
const dbreservation = computed(() => {
  return reservation.value * 2;
});
//  const dbreservation = computed(()=> reservation.value * 2) 객체 없어서 return 도 없음
const increaseReservation = () => {
  reservation.value++;
  // 이거 담을 필요 없이 바로 button 에서 써도 됨 += 1 , -= 1
};
// 2. 짐 보관 상태
const storage = reactive({
  isStored: false,
});
const toggleStorage = () => {
  storage.isStored = !storage.isStored;
};
// 3. 제빙기 청소 옵션 선택 및 요금 계산
const selectedOption = ref("basic");
const totalPrice = computed(() => (selectedOption.value === "basic" ? 50000 : 100000));
// 4. 고객 정보 관리 및 업데이트
const customer = reactive({
  name: "김철수",
  phone: "010-1234-5678",
});
const updateCustomer = () => {
  customer.name = "이영희";
  customer.phone = "011-8765-4321";
};
// 5. 남은 예약 가능 수
// 최대 예약 가능 수
const maxReservation = ref(10);
// 현재 예약 수
const currentReservation = ref(0);
// 남은 예약 가능 수
const remainingReservation = computed(() => maxReservation.value - currentReservation.value);
// ref 라서 value
const addReservation = () => {
  if (currentReservation.value < maxReservation.value) {
    currentReservation.value++;
  }
};
</script>
<template>
    <h1>2. Ex</h1>
  <div class="wrap">
    <!-- 1. 예약 카운트 증가 및 두배 표시 기능 -->
    <div class="ex">
      <h2>예약 관리</h2>
      <p>예약 수 : {{ reservation }}</p>
      <p>두배 예약 수 : {{ dbreservation }}</p>
      <button @click="increaseReservation">예약 추가</button>
    </div>
    <hr />
    <!-- 2. 짐 보관 상태 -->
    <div class="ex">
      <h2>짐 보관 상태</h2>
      <p>짐 보관 상태 : {{ storage.isStored ? "보관중" : "미보관" }}</p>
      <button @click="toggleStorage">짐 보관 토글</button>
    </div>
    <hr />
    <!-- 3. 제빙기 청소 옵션 선택 및 요금 계산 -->
    <div class="ex">
      <h2>제빙기 청소 예약</h2>
      <label>
        <select v-model="selectedOption">
          <option value="basic">기본 청소 (₩50,000)</option>
          <option value="deep">심층 청소 (₩100,000)</option>
        </select>
      </label>
      <p>선택한 요금 : {{ totalPrice }}원</p>
    </div>
    <hr />
    <!-- 4. 고객 정보 관리 및 업데이트 -->
    <div class="ex">
      <h2>고객 정보</h2>
      <p>고객 이름 : {{ customer.name }}</p>
      <p>전화번호 : {{ customer.phone }}</p>
      <button @click="updateCustomer">정보 변경</button>
    </div>
    <hr />
    <!-- 5. 남은 예약 가능 수 -->
    <div class="ex">
      <h2>예약 가능 여부</h2>
      <p>최대 예약 가능 수 : {{ maxReservation }}</p>
      <p>현재 예약 수 : {{ currentReservation }}</p>
      <p>남은 예약 가능 수 : {{ remainingReservation }}</p>
      <button @click="addReservation" :disabled="currentReservation >= maxReservation">예약 추가</button>
    </div>
  </div>
</template>
<style scoped>
.wrap {
  display: flex;
  gap: 20px;
}
.ex {
  flex: 1;
}
button {
  margin: 5px;
  padding: 8px 12px;
  border: none;
  background-color: #42b983;
  color: white;
  cursor: pointer;
  border-radius: 5px;
}
button:disabled{
    background-color: gray;
    cursor: not-allowed;
}
</style>

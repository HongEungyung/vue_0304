<script setup>
import { ref } from "vue";
const isVisible = ref(true);
const awesome = ref(true);
const type1 = ref("A");
// 단락표시
const ok = ref(true);
// 로그인 상태
const isLogin = ref(false);
const loginToggle = () => {
  isLogin.value = !isLogin.value;
};
// 예약 상태 버튼 변경
const isAvailable = ref(true);
// 날짜 선택
const selectDate = ref("");
</script>
<template>
  <div>
    <!-- v-if , v-show -->
    <h1>1. v-if , v-show</h1>
    <button @click="isVisible = !isVisible">토글</button>
    <p v-if="isVisible">
      v-if : 조건이 true 일 때만 표시 (조건이 false 면) DOM에서 완전히 제거 됨.
    </p>
    <!-- const 기본 설정이 지금 true 라서 "보이기"가 기본 설정. 버튼 누르면 사라짐 -->
    <p v-show="isVisible">
      v-show : 조건에 따라서 표시 (조건이 false 여도) DOM에 남아있으면서 display
      : none 으로 안보이기만 할 뿐.
    </p>
    <hr />

    <h1>2. If</h1>
    <div class="if">
      <button @click="awesome = !awesome">전환</button>
      <h2 v-if="awesome">Vue는 정말 멋지죠! 😻</h2>
      <h2 v-else>아닌가요? 😿</h2>
    </div>
    <hr />

    <h1>3. Else</h1>
    <div class="else">
      <div v-if="type1 === 'A'">A</div>
      <div v-else-if="type1 === 'B'">B</div>
      <div v-else-if="type1 === 'C'">C</div>
      <div v-else>A/B/C아님</div>
      <button @click="type1 = 'A'">A 선택</button>
      <button @click="type1 = 'B'">B 선택</button>
      <button @click="type1 = 'C'">C 선택</button>
      <button @click="type1 = 'D'">D 선택</button>
      <!-- === 같다는 표시 , = 는 type1 에 '알파벳'들을 담겠다는 표시 -->
    </div>
    <hr />

    <!-- 단락표시 -->
    <h1>4. 토글</h1>
    <h2>제목</h2>
    <button @click="ok = !ok">단락표시여부 토글</button>
    <div v-if="ok" class="info">
      <p>단락1</p>
      <p>단락2</p>
    </div>
    <hr />

    <!-- 로그인 상태에 따라 에약 버튼 보이기 -->
    <h1>5. 토글 / 버튼 변경</h1>
    <div>
      <button @click="loginToggle">
        {{ isLogin ? "로그아웃" : "로그인" }}
      </button>
      <p v-if="isLogin">환영합니다🥰</p>
      <button v-if="isLogin">예약하기</button>
      <p v-else>로그인 후 예약이 가능합니다😀</p>
    </div>
    <hr />

    <!-- 예약 가능 여부에 따라 버튼 다르게 보이기 -->
    <h1>6. 버튼 변경</h1>
    <div class="container">
      <h2>예약 가능 여부</h2>
      <p :class="{ available: isAvailable, unavailable: !isAvailable }">
        <!-- 객체 문법 (:class="{ 클래스명1 : 조건1, 클래스명2 : 조건2 }) -->
        {{
          isAvailable
            ? "현재 예약이 가능합니다."
            : "죄송합니다. 현재 예약이 마감되었습니다."
        }}
      </p>
      <button
        :class="{ reserve_btn: isAvailable, disabled_btn: !isAvailable }"
        @click="isAvailable = !isAvailable">
        {{ isAvailable ? "예약하기" : "예약불가" }}
      </button>
    </div>
    <hr />

    <!-- 날짜 선택 후 화면 보이기 -->
    <h1>7. 날짜 선택</h1>
    <div class="date-container">
      <h2>예약 날짜 선택</h2>
      <input type="date" class="date-input" v-model="selectDate" />
      <p :class="{ selected: selectDate, unselected: !selectDate }">
        {{
          selectDate ? `선택한 날짜 : ${selectDate}` : "날짜를 선택해주세요."
        }}
      </p>
    </div>
  </div>
</template>
<style scoped>
button {
  padding: 10px 20px;
  font-size: 16px;
  border: none;
  border-radius: 5px;
  cursor: pointer;
  transition: background 0.3s, transform 0.2s;
}
/* 단락표시 */
.info {
  background-color: antiquewhite;
  padding: 10px;
}
/* 예약하기 */
.available {
  color: #2ecc71;
}
.unavailable {
  color: #e74c3c;
}
.reserve_btn {
  background-color: #2ecc71;
  color: white;
}
.reserve_btn:hover {
  background-color: #01903d;
}
.disabled_btn {
  background-color: #bdc3c7;
  color: white;
  cursor: not-allowed;
}
/* 날짜선택 */
.date-input {
  padding: 10px;
  font-size: 16px;
  border: 2px solid #ccc;
  border-radius: 5px;
  outline: none;
  transition: all 0.3s;
}
.date-input:focus {
  border-color: #3498db;
}
.selected {
  color: #2ecc71;
  font-weight: bold;
}
.unselected {
  color: #e74c3c;
  font-weight: bold;
}
</style>

<script setup>
import { ref, reactive } from "vue";
const items = ref([
  { message: "Foo", children: ["A", "B"] },
  { message: "Bar", children: ["C", "D"] },
]);

// 2.
const parentMessage = ref("Parent");

// 3. 구조 분해 할당
const user = {
  name: "홍길동",
  age: 25,
  job: "개발자",
};
// 기존 방식
console.log(user.name); // :홍길동
console.log(user.age); // :25
// 구조 분해 할당 방식
const { name, age } = user;
// 기존 const 와 다르게 변수 선언 하는게 아니라 {} 객체 안으로 빌려와 쓰는 것
console.log(name); // :홍길동
console.log(age); // :25
console.log(user); // :▶{name: '홍길동', age: 25, job: '개발자'}

// 5.
const myObject = reactive({
  title: "Vue에서 목록을 작성하는 방법",
  //   ↑key: value↑
  author: "홍길동",
  publishedAt: "2016-04-10",
});

// 9.
// 할 일 목록 (isComplete 값에 따라 완료 여부 결정)
const todos = ref([
  { name: "청소하기", isComplete: false },
  { name: "공부하기", isComplete: true },
  { name: "운동하기", isComplete: false },
]);
</script>
<template>
  <div>
    <h2>v-for 리스트 예제 (import Vue_forList3)</h2>
    <h4>배열 안 객체들 안에 원하는 요소들 찾기</h4>
    <h3>1. 기본 리스트 반복</h3>
    <ul>
      <li v-for="item in items" :key="item.message">
        {{ item.message }}
        <ul>
          <li v-for="child in item.children" :key="child">
            <!-- 위에서 message 를 item에 담아놨기 때문에 -->
            {{ child }}
          </li>
        </ul>
      </li>
    </ul>
    <hr />

    <h3>2. 부모에 index 같이 출력</h3>
    <ul>
      <li v-for="(item, index) in items" :key="index">
        {{ parentMessage }} - {{ index }} - {{ item.message }}
      </li>
    </ul>
    <hr />

    <h3>3. 구조 분해 할당</h3>
    <!-- :객체나 배열에서 필요한 값만 골라서 변수에 저장하는 것 -->
    <ul>
      <li v-for="{ message } in items" :key="message">
        {{ message }}
      </li>
    </ul>
    <hr />

    <h3>4. 중첩 반복</h3>
    <ul>
      <!-- 부모 요소 반복 -->
      <li v-for="item in items" :key="item.message">
        <!-- 자식 요소 반복 -->
        <span v-for="childItem in item.children" :key="childItem">
          {{ item.message }} - {{ childItem }} <br />
        </span>
      </li>
    </ul>
    <hr />

    <h3>5. 객체 반복</h3>
    <ul>
      <!-- 객체의 키(key) 값(value)를 반복하여 출력 -->
      <li v-for="(value, key) in myObject" :key="key">
        {{ key }} : {{ value }}
      </li>
    </ul>
    <hr />

    <h3>6. 인덱스 + 객체 반복</h3>
    <ul>
      <!-- 객체의 키, 값(value)과 함께 index도 출력 -->
      <li v-for="(value, key, index) in myObject" :key="key">
        <!-- idnex숫자 . title : 내용 -->
        {{ index }}. {{ key }} : {{ value }}
      </li>
    </ul>
    <hr />

    <h3>7. 원하는 숫자만큼 반복</h3>
    <ul>
      <!-- 1-5까지 출력 -->
      <li v-for="number in 5" :key="number">
        {{ number }}
      </li>
    </ul>
    <hr />

    <h3>8. 탬플릿 사용</h3>
    <ul>
      <template v-for="item in items" :key="item.message">
        <li>{{ item.message }}</li>
      </template>
    </ul>
    <hr />

    <h3>9. 조건부 랜더링과 함께 사용</h3>
    <ul>
      <template v-for="todo in todos" :key="todo.name">
        <li v-if="!todo.isComplete">{{ todo.name }}</li>
        <!-- ↑ false 만 나오라는 뜻 -->
      </template>
    </ul>
    <hr />

    <h3>10. 탬플릿 태그를 활용한 조건부 랜더링</h3>
    <ul>
      <template v-for="todo in todos">
        <li v-if="!todo.isComplete" :key="todo.name">{{ todo.name }}</li>
        <!-- :key 가 li 안에 들어가는 게 오류가 덜 생기는 옳은 방법 -->
      </template>
    </ul>
    <hr />

    <h3>11. 다른 태그들을 활용한 v-for</h3>
    <ul>
      <!-- 다른 태그들을 사용해서 반복되는 리스트를 출력 -->
      <div v-for="item in items" :key="item.message">
        {{ item.message }}
      </div>
      <span v-for="item in items" :key="item.message">
        {{ item.message }}
      </span>
    </ul>
  </div>
</template>
<style scoped></style>

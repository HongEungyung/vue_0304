<script setup>
import { ref } from "vue";
const items = ref(["Apple", "Banana", "Cherry", "Orange", "Grapes"]);
// push()-추가
const addItem = ()=>{
    items.value.push("Pineapple")
}
// pop()-마지막 제거
const removeLastItem = ()=>{
    items.value.pop() // 배열의 마지막 애를 제거
}
// shift() - 첫 번째 제거
const removeFirstItem = ()=>{
    items.value.shift() // 배열의 첫번째 애를 제거
}
// unshift() - 첫 번째 추가
const addFirstItem = ()=>{
    items.value.unshift("mango")
}
// splice() - 요소 변경
const removeAndAddItem = ()=>{
    items.value.splice(1 , 2 , "Kiwi")
    // items.value.splice(index , delete개수 , "추가항목")
}
// sort() - 순차 정렬
const sortItems = ()=>{
    items.value.sort()
}
// reverse() - 역순 정렬
const reverseItems = ()=>{
    items.value.reverse()
}
// filter() - 'a' 포함된 요소만
const filterItems = ()=>{
    items.value = items.value.filter((item => item.includes("a")))
}
// concat() - 새로운 배열과 결합
const concatItems = ()=>{
    items.value = items.value.concat(["Strawberry" , "Blueberry"])
}
// slice() - 인덱스 1~2 요소 추출
const sliceItems = ()=>{
    items.value = items.value.slice(1, 3) // index 1, 2만 추출
    // items.value = items.value.slice(시작 index (포함), 끝 index (미포함)) 
    // 왜 이런식으로 만들었는지 이해X.

}
</script>

<template>
  <div>
    <h2>배열 조작 예제</h2>
    <p>현재 배열 : {{ items }}</p>
    <div class="btn-wrap">
    <button @click="addItem">push() - 추가</button>
    <button @click="removeLastItem">pop() - 마지막 제거</button>
    <button @click="removeFirstItem">shift() - 첫 번째 제거</button>
    <button @click="addFirstItem">unshift() - 첫 번째 추가</button>
    <button @click="removeAndAddItem">splice() - 요소 변경</button>
    <button @click="sortItems">sort() - 순차 정렬</button>
    <button @click="reverseItems">reverse() - 역순 정렬</button>
    <button @click="filterItems">filter() - 'a' 포함된 요소만</button>
    <button @click="concatItems">concat() - 새로운 배열과 결합</button>
    <button @click="sliceItems">slice() - 인덱스 1~2 요소 추출</button>
    </div>
  </div>
</template>

<style scoped>
button {
  margin: 5px;
  padding: 10px;
  border: none;
  background: rgb(133, 133, 255);
  color: white;
  cursor: pointer;
}
button:hover {
  background: rgb(74, 74, 198);
}
.btn-wrap{
    margin-top: 30px;
}
</style>

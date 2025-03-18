<script setup>
import {ref} from "vue"
const message = ref("안녕! 나는 vue야! 만나서 반가워!")
const message2 = ref("vue 첫 시간 연습 중...")
const message3 = ref("오늘 날씨 : 비")
const message4 = ref("3일 연휴 후 첫 수업 월요일 같은 화요일")
const count = ref(0)
const count2 = ref(0)
</script>
<template>
      <div>
    <h1>{{ message }}</h1>
    <h2>{{ message2 }}</h2>
    <p>{{ message3 }}</p>
    <span>{{ message4 }}</span>
    <span class="re_message">{{ message }}</span>
    <button @click="count++">클릭횟수+ {{ count }}</button>
    <button @click="count2--">클릭횟수- {{ count2 }}</button>
  </div>
</template>
<style scoped>
h1{
  color: rgb(255, 72, 179);
}
h2{
  color: violet;
}
p{
  color: yellowgreen;
}
span{
  color: green;
}
.re_message{
  display: block;
  color: rgb(76, 184, 151);
}
</style>
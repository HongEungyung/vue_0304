<script setup>
import {ref} from "vue"
const message = ref("")
const name = ref("")
const email = ref("")
const checked = ref(false)
const selected = ref("")
</script>
<template>
    <h1>4. V-model</h1>
    <div class="vModel">
    <input placeholder="입력하세요" v-model="message" @input="message = $event.target.value">
    <!-- 만든 사람이 외국인이라 한국어 오류남 그래서  @input="message = $event.target.value" 이거 써줌 (근데 난 이거 안써줘도 원래 됐음.) -->
    <p>입력한 값 : {{ message }}</p>
    <input placeholder="이름을 입력하세요" v-model="name" @input="name = $event.target.value">
    <input placeholder="이메일을 입력하세요" v-model="email">
    <p>{{ name }} 님의 {{ email }} 이메일입니다.</p>
    <hr>
    <label><input type="checkbox" v-model="checked">동의합니다.</label>
    <p>체크여부 : {{ checked }}</p>
    <hr>
    <select v-model="selected">
    <option value="apple">사과</option>
    <option value="banana">바나나</option>
    <option value="grape">포도</option>
    </select>
    <p>선택한 과일 : {{ selected }}</p>
    </div>
</template>
<style scoped>
.vModel{
    background-color: rgb(155, 255, 255);
    padding: 50px;
    margin-bottom: 50px;
}
</style>
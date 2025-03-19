<script setup>
import { useRouter } from 'vue-router';

const router = useRouter()
const goBack = ()=>{
router.go(-1) // -1 : 바로 직전 메뉴로 (아래 if 절과 함께)
// router.push("/") 바로 홈으로 가고 싶을 때 다 필요없고 이것만
if(window.history.length > 1){
  router.back()
}else{
  router.push("/")
}
}
</script>
<template>
    <div>
      <h1>메뉴 1</h1>
      <button @click="goBack">뒤로 가기</button>
    </div>
  </template>
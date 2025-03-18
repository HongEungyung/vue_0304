<script setup>
import { ref } from 'vue';
import ExArr_0313 from "./components/ExArr_0313.vue";
import Event from "./components/Event.vue";
// Event 토글
const showEx = ref(false)
</script>

<template>
  <div>
    <ExArr_0313 />
    <div class="event-wrap">
<button @click="showEx = !showEx" class="showEx-btn">
{{ showEx ? "닫기" : "Vue event 보기" }}
</button>
    <Event v-if="showEx" />
    </div>
  </div>
</template>

<style scoped>
.event-wrap{
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    padding-top: 60px;
}
.showEx-btn{
    margin-bottom: 30px;
}
</style>

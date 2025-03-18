<script setup>
import { ref } from "vue";
import TodoList_0313 from "./TodoList_0313.vue";
import ExArr_study from "./ExArr_study.vue";
const showTodoList = ref(false);
const showArr = ref(false);
</script>
<template>
  <div class="wrap">
    <div class="container">
      <h1>TodoList Ex</h1>
      <button @click="showTodoList = !showTodoList">
        {{ showTodoList ? "닫기" : "TodoList 보기" }}
      </button>
      <TodoList_0313 v-if="showTodoList" />
    </div>
    <hr />
    <div class="container">
      <h1>Array 공부</h1>
      <button @click="showArr = !showArr">
        {{ showArr ? "닫기" : "배열 예제보기" }}
      </button>
      <ExArr_study v-if="showArr"/>
    </div>
  </div>
</template>

<style scoped>
.wrap {
  background-color: antiquewhite;
  padding: 20px 0;
  display: flex;
  justify-content: center;
}
.container {
  flex: 1;
  text-align: center;
}
</style>

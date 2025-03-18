<script setup>
import { ref } from "vue";
// 할 일 목록 더미 데이터
const todos = ref([
  { id: 1, name: "Vue 공부하기", isComplete: false },
  { id: 2, name: "운동하기", isComplete: false },
  { id: 3, name: "책 읽기", isComplete: false },
]);
// 할 일 추가
const newTodo = ref("")
console.log(todos); // : 더미데이터 기존 배열 3개
const addTodo = ()=>{
    if(newTodo.value.trim()){
        todos.value.push({id: Date.now(), name: newTodo.value, isComplete: false})
        newTodo.value = "" // 입력 필드 초기화
        console.log(todos); // : 더미데이터에 더해서 내가 추가하 목록까지 배열 +플러스 됨
        
    }
}
// 할 일 완료 / 미완료
const toggleComplete = (todo)=>{
    todo.isComplete = !todo.isComplete
}
// 완료된 항목 삭제 기능
const deletecompleted = ()=>{
    todos.value = todos.value.filter(todo => !todo.isComplete)
}
</script>
<template>
  <div class="todo-wrap">
    <h2>📝 Todo List</h2>
    <!-- 할 일 입력 -->
    <div class="input-group">
      <input v-model="newTodo" placeholder="새로운 할 일 목록 입력..." />
      <button @click="addTodo">추가</button>
    </div>
    <h3>📌 진행 중</h3>
    <ul>
      <template v-for="todo in todos" :key="todo.id">
        <!-- for문을 돌리기 위해 오류방지용 template 태그 -->
        <li v-if="!todo.isComplete">
          <input type="checkbox" @change="toggleComplete(todo)" />
          {{ todo.name }}
        </li>
      </template>
    </ul>
    <!-- 완료된 할 일 목록 -->
    <h3>✅ 완료</h3>
    <ul>
      <template v-for="todo in todos" :key="todo.id">
        <li v-if="todo.isComplete">
          <input type="checkbox" checked @change="toggleComplete(todo)" />
          <del>{{ todo.name }}</del>
        </li>
      </template>
    </ul>
    <!-- 완료된 목록 삭제 -->
    <button @click="deletecompleted" class="delete-btn">완료된 항목 삭제</button>
  </div>
</template>
<style scoped>
.todo-wrap {
    display: flex;
    flex-direction: column;
    width: 300px;
    padding: 30px;
}
.input-group{
    display: flex;
    justify-content: space-between;
    margin: 10px 0;
}
button {
  padding: 5px 10px;
  cursor: pointer;
}
h3{
    text-align: left;
}
ul {
  padding: 0;
}
li {
  display: flex;
  align-items: center;
  gap: 5px;
  margin-bottom: 5px;
}
.delete-btn {
  margin-top: 10px;
  background: red;
  color: white;
  border: none;
  padding: 5px 10px;
}
</style>

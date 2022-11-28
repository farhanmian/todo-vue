<!-- @my-child:click="addTodoHandler"  -->
<template>
  <div class="todo">
    <div class="header">
      <h2>TODO</h2>
    </div>

    <div class="todoContainer">
      <TodoFormVue @add-todo:click="addTodoHandler" />

      <div class="todoItemContainer">
        <!-- @click="removeItem() -->
        <template v-for="todo in todos" :key="todo">
          <h2 class="todoItem" @click="removeItem(todo.id)">
            {{ todo.value }}
          </h2>
        </template>
      </div>
    </div>
  </div>
</template>

<script setup>
import { ref } from "vue";
import TodoFormVue from "./components/TodoForm.vue";

const todos = ref([]);

const addTodoHandler = (e) => {
  if (e.value.trim().length === 0) return;
  todos.value.push(e);
  console.log("addTodoHandler");
};

const removeItem = (id) => {
  todos.value = todos.value.filter((item) => item.id !== id);
  console.log("removeHandler");
};
</script>

<style scoped>
.header {
  background-color: #ff5e5e;
  text-align: center;
  padding: 2px 0;
  margin-bottom: 30px;
  box-shadow: 0 1px 2px rgba(0, 0, 0, 0.1);
  border-bottom: 1px solid #ddd;
}
.todo {
  max-width: 500px;
  height: 80vh;
  margin: auto;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  /* padding: 40px 10px; */
  border-radius: 5px;
}
.todoContainer {
  padding: 0 15px;
}
.todoItemContainer {
  margin-top: 50px;
}
.todoItem {
  background-color: #ff5e5e;
  padding: 6px 10px;
  border-radius: 2px;
  cursor: pointer;
  transition: all 0.3s;
}
.todoItem:hover {
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.15);
}
</style>

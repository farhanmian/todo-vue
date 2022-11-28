<template>
  <form @submit.prevent="$emit('add-todo:click', submitForm())" class="form">
    <input class="input" v-model.trim="inputValue" />
    <button class="addBtn">Add Todo</button>
  </form>

  <!-- <button @click="$emit('my-child:click', 'props')">testing</button> -->
</template>

<script setup>
import { ref } from "vue";
const inputValue = ref("");

defineEmits(["add-todo:click"]);

const submitForm = () => {
  const todoObj = {
    id: Math.ceil(Math.random() * 1000),
    value: inputValue.value,
  };
  console.log("submitForm");
  inputValue.value = "";

  return todoObj;
};
</script>

<style scoped>
.form {
  width: 100%;
  margin: auto;
  display: flex;
  justify-content: space-between;
}
.input {
  width: 75%;
  height: 30px;
  border-radius: 2px;
  margin-right: 20px;
  border-radius: 4px;
}
.input:hover,
.input:focus {
  outline: none;
}
.addBtn {
  padding: 4px 12px;
  background-color: #ff5e5e;
  border: none;
  /* border: 1px solid #757575; */
  border-radius: 3px;
  cursor: pointer;
  font-weight: 600;
  transition: all 0.2s;
}
.addBtn:hover {
  box-shadow: 0 2px 3px rgba(0, 0, 0, 0.2);
}
</style>

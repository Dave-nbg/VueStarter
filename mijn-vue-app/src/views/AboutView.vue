<template>
  <h1>Todo</h1>

  <label :for="TodoItem">Fill in your todo</label>
  <input :id="TodoItem" v-model="todoInput">
  <input type="button" @click="addItem()" value="Add" />
  <ul>
    <li v-for="(x,index) in todoText" :key=x>{{ x.text }}
      <input type="checkbox" value="{{x.completed}}">
      <input type="button" @click="deleteItem(index)" value="X" />
    </li>
  </ul>

</template>


<script setup>
import { ref } from 'vue';

const todoText = ref([{text: 'test', completed: false},{text: 'tester', completed: false}]);
const todoInput = ref('');

function addItem() {
  console.log(todoInput.value)
  if(todoInput.value !== ""){
    todoText.value.push({text: todoInput.value, completed: false});
    todoInput.value = '';
  }
}

function deleteItem(index){
  todoText.value.splice(index,1)
}





</script>

<script>

</script>


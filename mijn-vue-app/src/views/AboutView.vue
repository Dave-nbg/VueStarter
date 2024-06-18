<template>
  <ApiWeather/>

  <h1>Todo</h1>

  <label for="TodoItem">Fill in your todo</label> <!-- Line 2: Removed ':' from 'for' attribute -->
  <input id="TodoItem" v-model="todoInput"> <!-- Line 3: Removed ':' from 'id' attribute -->
  <input type="button" @click="addItem" value="Add" /> <!-- Line 4: Removed '()' from 'addItem' -->

  <ul>
    <ListItem
        v-for="(x, index) in todoText"
        :key="index"
        :index="index"
        :text="x.text"
        :completed="x.completed"
        @changeCompleted="changeCompleted"
        @deleteItemAdvanced="deleteItemAdvanced"
    />
  </ul>
</template>

<script setup>
import { ref } from 'vue';
import ListItem from "@/components/ListItem.vue";
import ApiWeather from "@/components/Api-weather.vue";

const todoText = ref([{ text: 'test', completed: false }, { text: 'tester', completed: false }]);
const todoInput = ref('');

function addItem() {
  if (todoInput.value !== "") {
    todoText.value.push({ text: todoInput.value, completed: false });
    todoInput.value = '';
  }
}

function deleteItem(index) {
  todoText.value.splice(index, 1);
}

function changeCompleted(index) {
  todoText.value[index].completed = !todoText.value[index].completed;
}

function deleteItemAdvanced(index) {
  deleteItem(index);
}
</script>

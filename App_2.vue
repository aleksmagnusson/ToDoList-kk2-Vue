<script setup>
import HelloWorld from "./components/HelloWorld.vue";
import { ref } from "vue";

// Making a let with the value of 0;
let id = 0;

// Puton in the functions.
const todos = ref([{ Text: "test", id: "1", done: true }]);
</script>

<template>
  <div id="app">
    <img alt="Harold logo" src="./assets/harold.png" style="width: 150px" />
    <h2>Kunskapskontroll 2, React - To Do List</h2>

    <ul>
      <li v-for="todo in todos" :key="todo.id">{{ todo.text }}</li>
    </ul>
  </div>
</template>

<style>
#app {
  font-family: "Comic Sans MS", "Comic Sans", cursive;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

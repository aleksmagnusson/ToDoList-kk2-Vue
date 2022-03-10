<script setup>
//import HelloWorld from "./components/HelloWorld.vue";
import { ref } from "vue";

const text = ref("");
const todos = ref([]);

function submit() {
  todos.value.push({ text: text.value, done: false });
  text.value = "";
}

function toggleTask(clickId) {
  todos.value = todos.value.map((item, id) => {
    if (clickId === id) {
      item.done = !item.done;
    }
    return item;
  });
}

function DeleteTask(clickId) {
  todos.value = todos.value.filter((item, id) => {
    if (clickId === id) {
      return false;
    }
    return true;
  });
}
// Puton in the functions.
</script>

<template>
  <div id="app">
    <img alt="Harold logo" src="./assets/harold.png" style="width: 150px" />
    <h2>Kunskapskontroll 2, React - To Do List</h2>
    <form @submit.prevent="submit()">
      <h2>Add a task todo:</h2>
      <input v-model="text" name="text" />
      <button>submit</button>
    </form>
    <ul>
      <li v-for="(todo, id) in todos" :key="id" :class="{ done: todo.done }">
        {{ todo.text }}
        <input type="checkbox" v-model="todo.done" @click="toggleTask(id)" />
        <button @click="DeleteTask(id)">Done</button>
      </li>
    </ul>
  </div>
</template>

<style>
#app {
  font-family: "Comic Sans MS", "Comic Sans", cursive;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #242424;
  margin-top: 60px;
}
.done {
  color: #f098f0;
}
</style>

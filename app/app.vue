<script>
import { defineNuxtComponent } from "#app";

export default defineNuxtComponent({
  data: () => ({
    todoList: [],
  }),
  methods: {
    fetchTodoList() {
      fetch("https://jsonplaceholder.typicode.com/todos")
        .then((response) => response.json())
        .then((json) => {
          this.todoList = json;
        });
    },
  },
});
</script>

<template>
  <div>
    <img src="todo.jpeg" alt="todo list" />
    <h1>Sup</h1>
    <button @click="fetchTodoList">Fetch!</button>
    <!-- <pre>
      {{ todoList }}
    </pre> -->
    <ul>
      <li v-for="todo in todoList" :key="`todo-id-${todo.id}`">
        <input type="checkbox" name="todo" :checked="todo.completed" />{{
          todo.title
        }}
      </li>
    </ul>
  </div>
</template>

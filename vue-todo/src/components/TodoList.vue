<template>
  <div class="container">
    <div class="width-container">
      <input
        v-model="todo_input"
        v-on:keyup.enter="addTodo(todo_input)"
      /><button v-on:click="addTodo(todo_input)">
        Add
      </button>
      <div v-for="(todo, index) in todos" :key="todo">
        <Todo
          v-bind:todo="todo"
          v-bind:index="index"
          @remove:todo="handleRemoveTodo"
        />
      </div>
    </div>
  </div>
</template>

<script>
import Todo from "./Todo";
import { ref } from "vue";

export default {
  name: "TodoList",
  props: {},
  setup: () => {
    let todos = ref(["Hello", "World"]);
    let todo_input = ref("");

    const addTodo = (todo) => {
      if (!todo) {
        return;
      }

      todos.value = [...todos.value, todo];
      todo_input.value = "";
    };

    const handleRemoveTodo = (key) => {
      todos.value = todos.value.filter((todo, index) => {
        return key !== index;
      });
    };

    return {
      todos,
      todo_input,
      addTodo,
      handleRemoveTodo,
    };
  },
  components: {
    Todo,
  },
};
</script>

<style scoped>
.container {
  display: flex;
  justify-content: center;
  align-content: center;
}

.width-container {
  max-width: 440px;
}
</style>

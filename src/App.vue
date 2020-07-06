<template>
  <div id="app">
    <Header />
    <TodoCounts :counts="counts" />
    <NewTodo @add-todo="addTodo" />
    <Todos :todos="todos" @del-todo="deleteTodo" :countTodo="countTodo" />
  </div>
</template>

<script>

import Header from "./components/Header";
import TodoCounts from "./components/TodoCounts";
import Todos from "./components/Todos";
import NewTodo from "./components/NewTodo";

export default {
  name: 'App',
  components: {
    Header,
    TodoCounts,
    Todos,
    NewTodo,
  },
  data() {
    return {
      todos: [],
      counts: [],
    }
  },
  methods: {
    deleteTodo(id) {
      this.todos = this.todos.filter(todo => todo.id !== id);
      this.countTodo();
    },
    addTodo(newTodo) {
      this.todos = [...this.todos, newTodo];
      this.countTodo();
    },
    countTodo() {
      let incomplete = this.todos.filter(todo => todo.completed === false);
      let complete = this.todos.filter(todo => todo.completed === true);
      this.counts = {
        total: this.todos.length,
        complete: complete.length,
        incomplete: incomplete.length,
      }
    }
  },
  mounted() {
    this.countTodo();
  }
}
</script>

<style>
* {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  line-height: 1.4;
  background-color: #0A0A0A;
}

.btn {
  display: inline-block;
  border: none;
  background: #555;
  color: #fff;
  padding: 7px 20px;
  cursor: pointer;
}

.btn:disabled {
  cursor: not-allowed;
}

.btn:hover {
  background: #666;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  color: #2c3e50;
  padding-top: 60px;
  width: 70vW;
  max-width: 70vW;
  margin: auto;
}
</style>

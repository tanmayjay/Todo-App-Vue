<template>
  <div>
    <p class="todo-item" v-bind:class="{'completed':todo.completed}">
        <input class="check-completed" type="checkbox" v-bind="{'checked':todo.completed}" @change="markCompleted" />
        <span class="title">{{ todo.title }}</span>
        <button class="delete" @click="$emit('del-todo', todo.id)">X</button>
    </p>
  </div>
</template>

<script>
  export default {
    name: "TodoItem",
    props: ["todo", "countTodo"],
    methods: {
        markCompleted() {
            this.todo.completed = ! this.todo.completed;
            this.countTodo();
        }
    },
  }
</script>

<style scoped>
  .todo-item {
      background: #f4f4f4;
      border-bottom: 1px double black;
      font-size: larger;
  }

  .title {
      margin: auto;
      font-weight: bold;
      font-size: larger;
  }

  .completed {
      text-decoration: line-through;
      color: #cbc;
  }

  .check-completed {
      margin: 1.2rem 0.5rem 1.2rem 0.5rem;
      height: 20px;
      width: 35px;
      opacity: 0.05;
  }

  .delete {
      background: none;
      color: #fa0022;
      display: none;
      border: none;
      border-radius: 5px;
      padding: 1px 4px 3px 4px;
      margin: 15px 5px 0 0;
      height: 28px;
      width: 28px;
      float: right;
      cursor: pointer;
      font-size: larger;
  }

  .delete:hover {
      border: 1px solid lightgray;
  }

  p:hover > .delete {
      display: block;
  }

  p:hover > .check-completed,
  .check-completed:checked,
  .check-completed:after {
      opacity: 1;
      background: red;
  }
</style>
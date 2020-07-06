<template>
  <div>
    <div v-bind:key="todo.id" v-for="todo in todos">
        <TodoItem :todo="todo" @del-todo="$emit('del-todo', todo.id)" :countTodo="countTodo" />
    </div>
  </div>
</template>

<script>
import TodoItem from "./TodoItem";

export default {
    name: "Todos",
    components: {
        TodoItem,
    },
    props: ["todos", "countTodo"],
}
</script>
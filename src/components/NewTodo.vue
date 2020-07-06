<template>
  <div>
    <form @submit="addTodo">
        <input type="text" name="title" v-model="title" placeholder="What to do?" required />
        <input type="submit" name="submit" class="btn" value="Add" :disabled="title.length < 1" />
    </form>
  </div>
</template>

<script>
import {v4 as uuid} from 'uuid';

export default {
    name: "NewTodo",
    data() {
        return {
            title: ''
        }
    },
    methods: {
        addTodo(e) {
            e.preventDefault();
            const newTodo = {
                id: uuid(),
                title: this.title,
                completed: false
            }
            this.$emit('add-todo', newTodo);

            this.title= '';
        }
    }
}
</script>

<style scoped>
form {
    display: flex;
}

input {
    height: 3.5rem;
    font-size: larger;
    padding: 5px;
    margin: 5px 0 5px 0;
}

input[type="submit"] {
    flex: 2;
}

input[type="text"] {
    flex: 10;
    padding-left: 1.4rem;
}
</style>
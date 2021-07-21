<template>
  <h1>Todo List</h1>

  <form @submit.prevent="onSubmit">
    <input type="text" placeholder="whatcha gonna do" v-model="inputValue" />
    <button type="submit">Add Todo</button>
  </form>

  <ol>
    <TodoItem
      v-for="todo in todos"
      :key="todo"
      :onDelete="() => deleteTodo(todo)"
      :todo="todo"
    />
  </ol>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import TodoItem from './components/TodoItem.vue'

type DataTypes = {
  todos: string[]
  inputValue: string
}

export default defineComponent({
  components: { TodoItem },
  name: 'App',
  data(): DataTypes {
    return {
      todos: [],
      inputValue: ''
    }
  },
  methods: {
    deleteTodo(todo: string) {
      this.todos.splice(this.todos.indexOf(todo), 1)
    },
    onSubmit() {
      if (this.todos.indexOf(this.inputValue) >= 0)
        return alert('Todo already exist')
      this.todos.push(this.inputValue)
      this.inputValue = ''
    }
  }
})
</script>

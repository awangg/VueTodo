
<!-- HTML -->
<!-- Structures -->
<template>
  <div>
    <p> Completed Tasks: {{ todos.filter(todo => { return todo.done }).length }} </p>
    <p> In Progress: {{ todos.filter(todo => { return !todo.done }).length }} </p>
    <todo v-for="todo in todos" :key="todo.id" v-bind:todo="todo" v-on:delete-todo="deleteTodo" v-on:complete-todo="completeTodo"></todo>
  </div>
</template>

<!-- JS -->
<!-- Events, Behavior, Data -->
<script type="text/javascript">
import Todo from './Todo'

export default {
  props: ['todos'],
  components: {
    Todo
  },
  methods: {
    deleteTodo (todo) {
      const todoIndex = this.todos.indexOf(todo)
      this.todos.splice(todoIndex, 1)
    },
    completeTodo (todo) {
      const todoIndex = this.todos.indexOf(todo)
      this.todos[todoIndex].done = true
    }
  }
}
</script>

<!-- CSS -->
<!-- Appearance -->
<style scoped>

</style>

<template>
  <div>
    <p>Completed Tasks: {{todos.filter(todo => { return todo.done === true }).length}}</p>
    <p>Pending Tasks: {{todos.filter(todo => { return todo.done === false }).length}}</p>
    <Todo
      v-for="(todo, index) in todos"
      :key="index"
      v-bind:todo="todo"
      v-on:deleteTodo="deleteTodo"
      v-on:toggleTodo="toggleTodo">
    </Todo>
  </div>
</template>

<script type = "text/javascript" >
import Todo from './Todo';

export default {
  props: ['todos'],
  components: {
    Todo,
  },
  methods: {
    deleteTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      this.todos.splice(todoIndex, 1);
    },
    toggleTodo(todo) {
      const todoIndex = this.todos.indexOf(todo);
      const currentTodo = this.todos[todoIndex];
      currentTodo.done = !currentTodo.done;
    },
  },
};
</script>
<style>
</style>

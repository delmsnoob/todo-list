<template>
  <div class="todos">
    <div v-bind:key="todo.id" v-for="todo in todos">
      <Todo
        :todo="todo"
        v-on:delete-todo="$emit('delete-todo', todo.id)"
      />
    </div>
  </div>
</template>

<script>
import Todo from './Todo'

export default {
  name: 'Todos',
  components: {
    Todo,
  },
  props: {
    todos: Array,
  }
}
</script>

<style scoped>
.todos {
  /* min-height: 300px; */
  padding: 40px;
}
</style>
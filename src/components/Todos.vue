<template>
  <div class="todos">
    <div v-bind:key="todo.id" v-for="todo in todos">
      <Todo
        @toggle-todo="$emit('toggle-todo', todo.id)"
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
  },
  emits: ['toggle-todo', 'delete-todo']
}
</script>

<style scoped>
.todos {
  /* min-height: 300px; */
  padding: 40px;
}
</style>
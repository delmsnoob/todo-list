<template>
    <div class="todos">
      <div v-bind:key="todo.id" v-for="todo in todos">
        <Todo v-bind:todo="todo" />
      </div>
    </div>
</template>

<script>
import Todo from './Todo'

export default {
    name: "Todos",
    components: {
      Todo
    },
    props: ["todos"]
}
</script>

<style scoped>
.todos {
  color: rgb(61, 60, 60);
  background: #e6cd69;
  padding: 1px 20px 10px 20px;
  box-shadow: .5px 1px 5px rgba(0, 0, 0, 0.57);
}
</style>
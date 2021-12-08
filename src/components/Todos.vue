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
  padding: 20px 0 20px 0;
}
</style>
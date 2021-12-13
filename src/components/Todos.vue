<template>
    <div class="todos__container">
      <AddTodo />
      <div class="todos">
        <div v-bind:key="todo.id" v-for="todo in todos">
          <Todo v-bind:todo="todo" v-on:delete-todo="$emit('delete-todo', todo.id)" />
        </div>
      </div>
      <div class="btn-container">
        <button class="btn add-task-btn" >
          <i class="add fas fa-plus"></i>
          New Task
        </button>
      </div>
    </div>
</template>

<script>
import Todo from './Todo'
import AddTodo from './AddTodo'

export default {
  name: 'Todos',
  components: {
    Todo,
    AddTodo
  },
  props: ["todos"],
  methods: {
    onSubmit(e) {
      e.preventDefault()
      return
    }
  }
}
</script>

<style scoped>
.todos {
  color: rgb(61, 60, 60);
  padding: 50px 0 50px 0;
  /* width: 100%; */
}

.todos--hide {
  display: none;
}

.btn-container {
  align-items: center;
  justify-content: center;
  display: flex;
  position: sticky;
}

.btn {
  position: sticky;
}

.add-task-btn {
  font-family: 'Open Sans';
  font-weight: bolder;
  position: absolute;
  width:200px;
  height: 60px;
  color: #fff;
  font-size: 1.2em;
  align-items: center;
  justify-content: center;
  text-align: center;
  background: #AF7EEB;
  border: 1px solid transparent;
  border-radius: 30px;
  box-shadow: 1px 1px 5px 1px rgba(0,0,0,0.51);
  cursor: pointer;
}

.btn:hover {
  background: rgb(160, 160, 228);
}

.add {
  margin-right: 8px;
}
</style>
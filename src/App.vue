<template>
  <div class="container">
    <Header title="Todo List"/>
    <Todos v-bind:todos="todos"/>
  </div>
</template>

<script>
import Header from './components/Header'
import Todos from './components/Todos'

export default {
  name: 'App',
  components: {
    Header,
    Todos,
  },
  data() {
    return {
      todos: [
        {
          id: 1,
          title: "Doctors Appointment",
          schedule: "March",
          completed: null
        },
        {
          id: 2,
          title: "Dentist Appointment",
          schedule: "March",
          completed: null
        },
        {
          id: 3,
          title: "Food shopping",
          schedule: "March",
          completed: null
        },
        {
          id: 4,
          title: "Pick up laundry",
          schedule: "March",
          completed: null
        }
      ]
    }
  }
}
</script>

<style>
* {
  user-select: none;
}

.container {
  font-family: 'Open Sans';
  max-width: 500px;
  margin: 30px auto;
  overflow: auto;
  min-height: 300px;
  border: 1px solid steelblue;
  box-shadow: 1px 1px 5px rgba(0, 0, 0, 0.57);
  padding: 30px;
  border-radius: 5px;
}
</style>

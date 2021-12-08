<template>
  <div class="container">
    <div class="container__header">
      <Header title="Todo List"/>
      <div class="container__body">
        <Todos v-bind:todos="todos"/>
      </div>
    </div>
    
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

body {
  user-select: none;
  background: #E3E9FF;
  font-family: 'Open Sans';
}

.container {
  display: grid;
  height: 90vh;
  justify-content: center;
  align-items: center;
  margin-right: auto;
  margin-left: auto;
}

.container__header {
  margin-right: auto;
  margin-left: auto;
}

.container__body {
  display: block;
  width: 100%;
  margin-top: 20px;
  background: #fff;
  justify-content: space-between;
  align-items: center;  
}
</style>

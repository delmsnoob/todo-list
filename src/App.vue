<template>
  <main>
    <div class="main__wrapper">
      <div class="content__header">
        <Header text="Website Todo"/>
      </div>
      <div class="body__wrapper">
        <transition name="fade">
          <Todos
            v-if="showAddTodo"
            v-bind:todos="todos"
            v-on:delete-todo="deleteTodo"
            @toggle-todo="toggleTodo"
          />
          <AddTodo
            v-if="!showAddTodo"
            @add-todo="addTodo"
          />
        </transition>
      </div>
      <div class="btn__wrapper">
        <ToggleAddTodo
          @toggle-click="toggleShowAddTodo"
          :text="showAddTodo ? 'New Task' : 'Close'" 
          class="btn"
        />
      </div>
      </div>
  </main>
</template>

<script>
import Header from './components/Header'
import Todos from './components/Todos'
import AddTodo from './components/AddTodo'
import ToggleAddTodo from './components/ToggleAddTodo'

export default {
  name: 'App',
  components: {
    Header,
    Todos,
    AddTodo,
    ToggleAddTodo,
  },
  data() {
    return {
      showAddTodo: true,
      "todos": []
    }
  },

  metaInfo () {
    const keywords = [
      'vue todo app',
      'todo app',
      'todo',
      'todoapp',
      'todolist',
      'vue',
      'vue todo',
      'vue todolist',
      'christian todo',
      'christian vue',
      'christian todo app',
      'christian todo app vue',
      'todo list vue',
      'vue todo list',
      'christian todolist',
      'christian todolist vue',
      'simple todo app',
      'simple todo app vue',
      'vue simple todo',
      'christian simple todo vue',
      'christian simple todo app vue',
      'christian simple todo list app vue',
      'todo list template',
      'todo list app',
      'todo list',
      'daily todo list',
      'create a todo list',
      'online todo',
      'online todo list',
      'online todo list app vue',
      'todo list template vue',
      'make a todo',
      'make a todo list vue',
      'make a todo app vue',
      'todo list online',
      'my todo list',
      'free todo list',
    ]
    return {
      title: 'Simple TodoApp using Vue',
      meta: [
        { name: 'todoapp', vmid: 'todoapp', content: 'Simple TodoApp using Vue' },
        { name: 'description', content: 'Simple Todo list app using Vue. Add new todo and mark it when finished. You can delete a todo when you marked it as finished. Manage your daily tasks effectively' },
        { name: 'keywords', content: keywords },
        { name: 'google-site-verification', content: 'TqPrL8LFuVWrwVh7l1gXf_g4_H7WwC0Jb0LfpEpU_DM' },
        { property: 'og:type', content: "website" },
        { property: 'og:title', content: "Simple TodoApp Using Vue" },
        { property: 'og:description', content: "Simple Todo list app using Vue" },
        { property: 'og:url', content: "https://christian-todoapp.netlify.app" },
        { property: 'og:site_name', content: "Simple TodoApp Using Vue" },

      ]
    }
  },

  async created() {
    this.todos = await this.fetchTodos()
  },
  methods: {
    async fetchTodos() {
      const res = await fetch('http://localhost:5000/todos')

      const data = await res.json()

      return data
    },
    async fetchTodo(id) {
      const res = await fetch(`http://localhost:5000/todos/${id}`)

      const data = await res.json()

      return data
    },
    toggleShowAddTodo() {
      this.showAddTodo = !this.showAddTodo
    },
    async deleteTodo(id) {
      if (confirm('Are you sure?')) {
        const res = await fetch(`http://localhost:5000/todos/${id}`, {
          method: 'DELETE'
        })

        res.status === 200 ? (this.todos = this.todos.filter(todo => todo.id !== id)) : alert('Error deleting todo')
      }
    },
    async addTodo(todo) {
      const res = await fetch('http://localhost:5000/todos', {
        method: 'POST',
        headers: {
          'Content-type': 'application/json',
        },
        body: JSON.stringify(todo)
      })

      const data = await res.json()

      alert('Todo has been successfully added')
      this.todos = [...this.todos, data]
    },
    async toggleTodo(id) {
      const todoToToggle = await this.fetchTodo(id)
      const updateTodo = { ...todoToToggle, is_completed: !todoToToggle.is_completed }

      const res = await fetch(`http://localhost:5000/todos/${id}`, {
        method: 'PUT',
        headers: {
          'Content-type': 'application/json',
        },
        body: JSON.stringify(updateTodo)
      })

      const data = await res.json()

      return data
      // data = this.data.map((data) => {
      //   data.id === id ? { ...data, is_completed: data.is_completed } : todos
      // })
    }
  }
}
</script>

<style>
body {
  background: #E3E9FF;
  font-family: 'Open Sans';
  margin: auto;
}

main {
  display: flex;
  justify-content: center;
  align-items: center;
  height: 90vh;
  overflow: hidden;
}

button, input[type="text"] {
  font-family: 'Open Sans';
}

.main__wrapper {
  width: 31.25rem;
  margin: 10px;
}

.body__wrapper {
  display: flex;
  /* justify-content: center; */
  align-items: center;
  /* text-align: left; */
  margin-top: 20px;
  background: #fff;
  min-height: 150px;
}

.btn__wrapper {
  display: flex;
  justify-content: center;
  align-items: center;
  position: relative;
}

.btn {
  font-family: 'Open Sans';
  position: absolute;
  font-weight: bold;
  font-size: 1.2em;
  width: 200px;
  height: 60px;
  color: #fff;
  background: #af7eeb;
  border: 1px solid transparent;
  border-radius: 30px;
  box-shadow: 1px 1px 5px 1px rgba(0,0,0,0.51);
  cursor: pointer;
  }

.btn:hover {
  background: #c198eb;
}

.fas {
  color: black;
}

.fade-enter-active, .fade-leve-active {
  transition: opacity 1s;
}

.fade-enter, .fade-leave-to {
  opacity: 0;
}
</style>
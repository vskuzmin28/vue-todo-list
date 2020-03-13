<template lang="pug">
  .main
    h2 TODOs app
    hr
    router-link(to="/") Home
    hr
    CreateTodoItem(
      @add-todo="addTodo"
    )
    hr
    Loader(v-if="loading")
    TodoList(
      v-else-if="todos.length"
      v-bind:todos="todos" 
      @remove-todo="removeTodo"
    )
    p(v-else) No todos!
</template>

<script>
import TodoList from '@/components/TodoList.vue'
import CreateTodoItem from '@/components/CreateTodoItem.vue'
import Loader from '@/components/Loader.vue'

export default {
  name: 'App',
  data() {
    return {
      todos: [],
      loading: true
    }
  },
  components: {
    TodoList, CreateTodoItem, Loader
  },
  mounted() {
      fetch('https://jsonplaceholder.typicode.com/todos?_limit=10')
        .then(response => response.json())
        .then(json => {
          setTimeout(() =>{
            this.todos = json
            this.loading = false
          }, 1500)
        })
  },
  methods: {
    removeTodo(id) {
      this.todos = this.todos.filter(t => t.id !== id)
    },
    addTodo(todo) {
      this.todos.push(todo)
    }
  }
}
</script>
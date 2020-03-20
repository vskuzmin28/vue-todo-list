<template lang="pug">
  .main
    h2 TODOs app
    hr
    router-link(to="/") Home
    hr
    .main__head
      CreateTodoItem(
        @add-todo="addTodo"
      )
      select(v-model="filter")
        option(value="completed") Completed
        option(value="not-completed") Not completed
        option(value="all") All
    hr
    Loader(v-if="loading")
    TodoList(
      v-else-if="filteredTodos.length"
      v-bind:todos="filteredTodos" 
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
      loading: true,
      filter: 'all'
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
  computed: {
    filteredTodos: function() {
      if (this.filter === 'all') {
        return this.todos
      }

      if (this.filter === 'completed') {
        return this.todos.filter(t => t.completed)
      }

      if (this.filter === 'not-completed') {
        return this.todos.filter(t => !t.completed)
      }
      return this.length;
    }
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

<style lang="scss" scoped>
  .main__head {
    display: flex;
    flex-direction: row;
    justify-content: center;

    &-form {
      margin-right: 10px;
    }

  }
</style>
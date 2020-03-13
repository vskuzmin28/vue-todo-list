<template lang="pug">
  .main
    h2 TODOs app
    hr
    CreateTodoItem(
      @add-todo="addTodo"
    )
    hr
    TodoList(
      v-if="todos.length"
      v-bind:todos="todos" 
      @remove-todo="removeTodo"
    )
    p(v-else) NETU AZAZA
</template>

<script>
import TodoList from '@/components/TodoList.vue'
import CreateTodoItem from '@/components/CreateTodoItem.vue'

export default {
  name: 'App',
  data() {
    return {
      todos: [
        // {id: 1, title: 'Simple title', completed: false},
        // {id: 2, title: 'Simple title2', completed: false},
        // {id: 3, title: 'Simple title3', completed: false}
      ]
    }
  },
  components: {
    TodoList,
    CreateTodoItem
  },
  mounted() {
      fetch('https://jsonplaceholder.typicode.com/todos?_limit=10')
        .then(response => response.json())
        .then(json => {
          this.todos = json
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
<template lang="pug">
  .main
    h2 Tasks
    
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

    hr
    router-link(class='link' to="/") Go to home
</template>

<script>
import TodoList from '@/components/TodoList.vue'
import CreateTodoItem from '@/components/CreateTodoItem.vue'
import Loader from '@/components/Loader.vue'

export default {
  name: 'App',
  data() {
    return {
      todos: [
        {id: 0, title: "Make dinner tonight!", completed: true},
        {id: 1, title: "Fold the laundry.", completed: false},
        {id: 2, title: "Learn to make a Vue app!", completed: false},
        {id: 3, title: "Todo # 3", completed: false},
        {id: 4, title: "Todo # 4", completed: false},
        {id: 5, title: "Todo # 5", completed: true},
        {id: 6, title: "Todo # 6", completed: true},
        {id: 7, title: "Todo # 7", completed: false},
        {id: 8, title: "Todo # 8", completed: false},
        {id: 9, title: "Todo # 9", completed: false},
        {id: 10, title: "Todo # 10", completed: false},
        {id: 11, title: "Todo # 11", completed: true},
        {id: 12, title: "Todo # 12", completed: false}
      ],
      loading: false,
      filter: 'all'
    }
  },
  components: {
    TodoList, CreateTodoItem, Loader
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
    justify-content: space-between;

    &-form {
      margin-right: 10px;
    }

  }
</style>
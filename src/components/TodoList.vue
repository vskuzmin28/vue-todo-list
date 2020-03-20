<template lang="pug">
    ul
        TodoListItem(
            v-for="(todo, i) in todos" :key="todo.id"
            v-bind:index="i"
            v-bind:todo="todo"
            v-on:remove-todo="removeTodo"
        )
</template>

<script>
import TodoListItem from '@/components/TodoListItem.vue'
export default {
    props: ['todos'],
    components: {
        TodoListItem
    },
    methods: {
        removeTodo(id) {
            this.$emit('remove-todo', id)
        }
    }
}
</script>

<style lang='scss' scoped>
    ul {
        margin: 0;
        padding: 0 10px;
    }
</style>
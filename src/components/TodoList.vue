<template lang="pug">
    ul(class="list")
        TodoListItem(
            class='list__item'
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

<style lang='scss'>
    .list {
        margin: 0;
        padding: 0 0px;

        &__item {
            margin: 0;
            margin-bottom: 10px;
            padding: 0;
            padding-bottom: 10px;
            display: flex;
            flex-direction: row;
            align-items: center;
            height: 20px;
            border-bottom: 1px solid #e3e3e3;

            &:last-child {
                border: 0;
                margin-bottom: 0;
                padding-bottom: 0;
            }


            &-button {
                height: 30px;
                padding: 0 15px 0 35px;
                border-radius: 2em;
                display: inline-flex;

                align-items: center;
                color: #fff;
                background: #4fc08d;
                transition: all 0.15s ease;
                box-sizing: border-box;
                border: 1px solid #4fc08d;
                cursor: pointer;
                outline: none;

                svg {
                    width: 40px;
                    height: 20px;
                    margin-left: -20px;
                }

                &_remove {
                    background: #c72e2e;
                    border-color: #c72e2e;

                    &:hover {
                        background: #4fc08d;
                        border: 1px solid #4fc08d;
                    }

                }

            }

        }

    }
    
</style>
<template lang="pug">
    li(v-bind:class="{done: todo.completed}")
        input(
            type="checkbox"
            @v-on="todo.completed = !todo.completed"
            v-model="todo.completed"
            :id="index"
        )
        label(:for="index")
            span {{index + 1}}
            p {{todo.title | uppercase}}
        button.list__item-button.list__item-button_remove(v-on:click="$emit('remove-todo', todo.id)")
            svg(xmlns='http://www.w3.org/2000/svg' width='14' height='14' viewbox='0 0 14 14' fill='#fff')
                path(d='M14.53 4.53l-1.06-1.06L9 7.94 4.53 3.47 3.47 4.53 7.94 9l-4.47 4.47 1.06 1.06L9 10.06l4.47 4.47 1.06-1.06L10.06 9z')


</template>

<script>
import iconClose from '@/assets/close.svg';
export default {
    data() {
        return {
            iconClose
        }
    },
    props: {
        todo: {
            type: Object,
            required: true
        },
        index: Number
    },
    filters: {
        uppercase(value) {
            return value.toUpperCase()
        }
    }
}
</script>

<style lang="scss" scoped>
    span {
        margin: 0 10px;
        font-weight: bold;
    }

    label {
        flex-grow: 1;
        display: flex;
        flex-direction: row;
        align-items: center;

        p {
            text-align: left;
        }

    }

    button {
        display: flex;
        align-items: center;
        justify-content: center;
        width: 20px;
        height: 100%;
    }

    .done {
        text-decoration: line-through;

        button, .remove {
            text-decoration: none !important;
        }

    }

    .remove {
        background: red;
        text-decoration: none;
    }

</style>
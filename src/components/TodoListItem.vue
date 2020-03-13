<template lang="pug">
    li(v-bind:class="{done: todo.completed}")
        input(
            type="checkbox"
            @change="todo.completed = !todo.completed"
            v-model="todo.completed"
            :id="index"
        )
        label(:for="index")
            span {{index + 1}}
            p {{todo.title | uppercase}}
        button.remove(v-on:click="$emit('remove-todo', todo.id)") &times;
</template>

<script>
export default {
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

<style lang="scss">
    li {
        margin: 0;
        margin-bottom: 20px;
        padding: 0;
        display: flex;
        flex-direction: row;
        align-items: center;
        height: 20px;

        &:last-child {
            margin-bottom: 0;
        }

    }

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
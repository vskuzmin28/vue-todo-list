<template lang='pug'>
    form(@submit.prevent="onSubmit" class='main__head-form')
        input(type="text" v-model="title")
        button(type="submit") Create
</template>

<script>
export default {
    data() {
        return {
            title: ''
        }
    },
    methods: {
        onSubmit() {
            if (this.title.trim()) {
                const newTodo = {
                    id: Date.now(),
                    title: this.title,
                    completed: false
                }

                this.$emit('add-todo', newTodo)
                this.title = ''
            }
        }
    }
}
</script>

<style lang="scss" scoped>
    form {
        display: flex;
        flex-direction: row;
        justify-content: center;

        button {
            width: 150px;
        }

    }
</style>
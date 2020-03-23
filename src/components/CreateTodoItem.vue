<template lang='pug'>
    form(@submit.prevent="onSubmit" class='main__head-form')
        input.form__input(type="text" v-model="title"  :placeholder="[[ placeholderValue ]]")
        button(type="submit") Create
</template>

<script>
export default {
    data() {
        return {
            title: '',
            placeholderValue: 'Enter task name'
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
            height: 30px;
            padding: 0 35px;
            border-radius: 2em;
            display: inline-flex;
            align-items: center;
            color: #fff;
            background-color: #4fc08d;
            transition: all 0.15s ease;
            box-sizing: border-box;
            border: 1px solid #4fc08d;
            cursor: pointer;
            outline: none;

            &:hover {
                background: #35495e;
                border-color: #35495e;
            }

        }

        input {
            height: 30px;
            line-height: 30px;
            box-sizing: border-box;
            padding: 0 15px 0 15px;
            border: 1px solid #e3e3e3;
            color: #273849;
            outline: none;
            border-radius: 15px;
            margin-right: 10px;
            transition: border-color 0.2s ease;

            &:hover, &:focus {
                border-color: #35495e;
            }
        }

    }
</style>
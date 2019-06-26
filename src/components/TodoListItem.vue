<template>
        <div class="todo-list-item">
              <input type="checkbox" v-model="todo.completed" class="completeTodo">
               <div class="todoText" v-if="!todo.editing">{{todo.text}}</div>
               <input v-focus type="text" v-model="todo.text" v-else class="todoEditing" @keyup.enter="saveEdit(todo)" @blur="saveEdit(todo)" @keyup.esc="cancelEdit(todo)">
               <button @click="editTodo(todo)" class="editTodo">Z</button>
           <button @click="deleteTodo(todo)" class="deleteTodo">X</button>

        </div>
</template>

<script>
export default {
    props: ['todo'],
    data() {
        return {
            beforeEdit: '',
        }
    },
    methods: {
        deleteTodo(todo) {
            this.$emit('delete-todo', todo)
        },
        saveEdit(todo) {
            if (todo.text == '') {
                todo.text = this.beforeEdit
            }
            todo.editing = false
        },
        editTodo(todo) {
            this.beforeEdit = todo.text
            todo.editing = true
        },
        cancelEdit(todo) {
            todo.text = this.beforeEdit
            todo.editing = false
            
        }
    },
    directives: {
        focus: {
            // directive definition
            inserted: function (el) {
            el.focus()
            }
        }
    }
}
</script>

<style>
    .todo-list-item {
        border: 1px solid #ccc;
        margin: 5px 0;
        font-size: 19px;
        position: relative;
    }
    .todoText {
               padding: 8px 12px 8px 35px;
    }
    .completeTodo {
        position: absolute;
        left: 8px;
        top: 8px;
    }
    .deleteTodo {
        position: absolute;
        right: 8px;
        top: 8px;
    }
    .editTodo {
        position: absolute;
        right: 35px;
        top: 8px;
    }
    .todoEditing {
        padding: 8px 12px 8px 35px;
        font-size: 19px;
        box-sizing: border-box;
        border: none;
        outline: -webkit-focus-ring-color auto 1px;
    }
</style>

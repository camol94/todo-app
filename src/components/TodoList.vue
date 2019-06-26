<template>
        <div class="todo-list">
            <TodoListItem v-for="todo in todos" :todo.sync="todo" v-on:delete-todo="deleteTodo"></TodoListItem>
        </div>
</template>
<script>
import TodoListItem from './TodoListItem.vue';
export default {
    props: ['todos'],
    components: {
        TodoListItem
    },
    methods: {
        deleteTodo(todo) {
            this.todos.splice(this.todos.indexOf(todo), 1);
        }
    }
    
}
</script>
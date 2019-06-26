<template>
    <div class="todo-informations">
        Todos: {{todos.length}}<br>
        Completed: {{todos.filter(todo => {return todo.completed === true}).length}}<br>
        Active: {{todos.filter(todo => {return todo.completed === false}).length}}
    </div>
</template>

<script>
export default {
    props: ['todos'],
    data() {
        return {
            
        }
    }
}
</script>
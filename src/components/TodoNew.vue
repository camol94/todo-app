<template>
    <div class="todoNew">
        <input type="checkbox" class="toggleAll">
        <input type="text" class="newTodo" v-model="newTodo" @keyup.enter="addNewTodo()" placeholder="Add new task here...">
    </div>
</template>

<script>
export default {
    data() {
        return {
            newTodo: '',
        }
    },
    methods: {
        addNewTodo() {
            if (this.newTodo != '') {
                const todo = this.newTodo;
                this.$emit('sendTodo', {
                text: todo,
                completed: false,
                editing: false
            });
            } else {
                console.log('Empty task.')
                return
            }
            
            this.newTodo = ''
        }
    }
}
</script>
<style scoped>
    .todoNew {
        position: relative;
        /* padding: 8px 12px; */
    }
    .toggleAll {
        position: absolute;
        top: 11px;
        left: 9px;        
    }
    .newTodo {
        width: 100%;
        padding: 8px 12px 8px 35px;
        font-size: 19px;
    }
</style>
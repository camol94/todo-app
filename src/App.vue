<template>
  <div id="app">
    <img alt="Vue logo" src="./assets/logo.png">
    <h1>{{title}}</h1>
    <TodoNew v-on:sendTodo="sendTodo" />
    <TodoList v-bind:todos="todosFilter"/>
    <TodoFilters v-bind:filter="filter" v-on:filterAll="filterAll" v-on:filterActive="filterActive" v-on:filterCompleted="filterCompleted" />
    <TodoInformations v-bind:todos="todos" />    
  </div>
</template>

<script>
import TodoNew from './components/TodoNew.vue'
import TodoList from './components/TodoList.vue'
import TodoFilters from './components/TodoFilters.vue'
import TodoInformations from './components/TodoInformations.vue'

export default {
  name: 'app',
  components: {
    TodoNew,
    TodoList,
    TodoFilters,
    TodoInformations
  },
  data() {
    return {
      title: 'Kamil Bała Todo-App',
      filter: 'all',
      todos: [
        {
          text: 'Todo 1',
          completed: false,
          editing: false
        },
        {
          text: 'Todo 2',
          completed: true,
          editing: false
        },
        {
          text: 'Todo 3',
          completed: true,
          editing: false
        }
      ]
    }
  },
  methods: {
    sendTodo(newTodo) {
      this.todos.push(newTodo);
    },
    filterAll() {
      this.filter = 'all'
    },
    filterActive() {
      this.filter = 'active'
    },
    filterCompleted() {
      this.filter = 'completed'
    } 
  },
  computed: {
    todosFilter() {
      if (this.filter == 'all') {
        return this.todos        
      } else if (this.filter == 'active') {
        return this.todos.filter(todo => !todo.completed)
      } else if (this.filter == 'completed') {
        return this.todos.filter(todo => todo.completed)
      }
    }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;

  color: #2c3e50;
  margin-top: 60px;
  border: 1px solid #ccc;
  width: 480px;
  margin: 0 auto;
  padding: 10px;
}
* {
  box-sizing: border-box;
}
</style>

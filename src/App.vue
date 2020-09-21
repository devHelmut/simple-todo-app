<template>
  <div id="app">
    <Header class="header" title="TODO App" />
    <TodoAdd class="todo-add" />
    <TodosList class="todo-list" @del-todo="deleteTodo" :todos="todos" />
  </div>
</template>

<script>
  import Header from './components/Header';
  import TodosList from './components/TodosList';
  import TodoAdd from './components/TodoAdd';

  export default {
    name: 'App',
    components: {
      Header,
      TodosList,
      TodoAdd,
    },
    data() {
      return {
        todos: [
          {
            id: 0,
            title: 'Some task',
            completed: false,
          },
          {
            id: 1,
            title: 'Some task',
            completed: true,
          },
          {
            id: 2,
            title: 'Some task',
            completed: false,
          },
          {
            id: 3,
            title: 'Some task',
            completed: false,
          },
        ],
      };
    },
    methods: {
      deleteTodo(id) {
        this.todos = this.todos.filter(el => el.id !== id);
      }
    },
  };
</script>

<style>
  body {
    margin: 0;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
  }

  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    width: 30rem;
    border-radius: 10px;
    overflow: hidden;
  }

  header,
  todo-add {
    margin-bottom: 0.5rem;
  }
</style>

<template>
  <div id="app">
    <Header class="header" title="TODO App" />
    <TodoAdd class="todo-add" @add-todo="addTodo" />
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
            title: 'Some ordinary task that u may not even complete',
            completed: false,
          },
          {
            id: 1,
            title: 'Some ordinary task that u may not even complete',
            completed: true,
          },
          {
            id: 2,
            title: 'Some ordinary task that u may not even complete',
            completed: false,
          },
          {
            id: 3,
            title: 'Some ordinary task that u may not even complete',
            completed: false,
          },
          {
            id: 4,
            title: 'Some ordinary task that u may not even complete',
            completed: false,
          },
        ],
        availableIds: [],
      };
    },
    methods: {
      deleteTodo(id) {
        this.todos = this.todos.filter((el) => el.id !== id);
        this.availableIds.push(id);
      },
      addTodo(title) {
        const newTodo = {
          id: this.availableIds == false ? this.todos.length : this.availableIds.pop(),
          title,
          completed: false,
        };
        this.todos.push(newTodo);
      },
    },
  };
</script>

<style lang="scss">
  body {
    margin: 0;
    display: flex;
    justify-content: center;
    min-height: 100vh;

    @media screen and (min-width: 450px) {
      // padding: 1rem 0 0;
      align-items: center;
    }
  }

  #app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    width: 30rem;
    overflow: hidden;

    @media screen and (min-width: 450px) {
      border-radius: 10px;
      margin: 1rem 0;
    }
  }

  .header,
  .todo-add {
    margin-bottom: 0.7rem;
  }
</style>

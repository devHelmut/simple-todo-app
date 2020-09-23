<template>
  <ul class="todos-list">
    <TodoItem
      class="todo-item"
      @del-todo="$emit('del-todo', todo.id)"
      v-for="todo in todos"
      :key="todo.id"
      :todo="todo"
    />
  </ul>
</template>

<script>
  import TodoItem from './TodoItem';

  export default {
    name: 'TodoList',
    components: {
      TodoItem,
    },
    props: ['todos'],
  };
</script>

<style scoped lang="scss">
  ul {
    list-style: none;
    margin: 0;
    padding: 0;

    .todo-item:not(:last-child) {
      margin-bottom: 0.3rem;
    }
  }
</style>

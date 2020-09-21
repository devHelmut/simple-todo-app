<template>
  <li class="todo-item" :class="{ completed: todo.completed }">
    <input
      @change="changeComplete"
      type="checkbox"
      name="todo-item"
      :id="`todo-item${todo.id}`"
      :checked="todo.completed"
    />
    <label :for="`todo-item${todo.id}`">{{ todo.title }}</label>
    <button class="del-btn" @click="$emit('del-todo', todo.id)">X</button>
  </li>
</template>

<script>
  export default {
    name: 'Todo',
    props: ['todo'],
    methods: {
      changeComplete() {
        this.todo.completed = !this.todo.completed;
      },
    },
  };
</script>

<style scoped lang="scss">
  ::selection {
    background: #000;
    color: #fff;
  }

  .todo-item {
    position: relative;
    font-size: 1.5rem;
    letter-spacing: 1px;
    background: #ccc;
    cursor: pointer;
    padding: 1rem;

    * {
      cursor: pointer;
    }

    input {
      transform: scale(1.5);
      margin-right: 1rem;
    }

    .del-btn {
      position: absolute;
      right: 0.5rem;
      top: 50%;
      transform: translatey(-50%);
      background: rgba(255, 0, 0, 0.6);
      border: none;
      border-radius: 50%;
      text-align: center;
      padding: 0.3rem 0.5rem;
      font-family: monospace;
      font-weight: 700;
      color: rgba(0,0,0,0.8);

      &:focus {
        outline: none;
        box-shadow: 0 0 5px black;
      }
    }

    &.completed {
      text-decoration: line-through;
    }
  }
</style>

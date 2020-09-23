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
    <button class="del-btn" @click="$emit('del-todo', todo.id)">x</button>
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
    font-size: 1.1rem;
    letter-spacing: 0px;
    background: #ddd;
    cursor: pointer;
    padding: 1rem 0.5rem;
    display: grid;
    grid-template-columns: 1.7rem 1fr 2rem;
    align-items: center;

    @media screen and (min-width: 450px) {
      grid-template-columns: 2rem 1fr 2.5rem;
      font-size: 1.5rem;
      letter-spacing: 1px;
      padding: 1rem;
    }

    * {
      cursor: pointer;
    }

    input {
      transform: scale(1.5);
      margin-right: 1rem;
    }

    .del-btn {
      background: rgba(255, 0, 0, 0.6);
      border: none;
      border-radius: 50%;
      display: flex;
      justify-content: center;
      align-items: center;
      padding: 0.3rem 0.5rem;
      font-family: monospace;
      font-weight: 700;
      color: rgba(0, 0, 0, 0.8);
      font-size: 1.5rem;
      width: 32px;
      height: 32px;

      &:focus {
        outline: none;
        box-shadow: 0 0 5px black;
      }
    }

    &.completed label {
      text-decoration: line-through;
    }
  }
</style>

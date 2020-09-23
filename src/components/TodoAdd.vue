<template>
  <div class="todo-add">
    <form @submit="addTodo">
      <input type="text" v-model="title" placeholder="do something..." />
      <input type="submit" value="Add todo" />
    </form>
  </div>
</template>

<script>
  export default {
    name: 'TodoAdd',
    data() {
      return {
        title: '',
      };
    },
    methods: {
      addTodo(ev) {
        ev.preventDefault();
        if (this.title !== '') {
          this.$emit('add-todo', this.title);
          this.title = '';
        }
      },
    },
  };
</script>

<style lang="scss" scoped>
  .todo-add form {
    display: grid;
    height: 8rem;
    grid-template-columns: 1fr;
    grid-template-rows: 4rem 4rem;

    @media screen and (min-width: 350px) {
      height: 4rem;
      grid-template-columns: 1fr 6rem;
    }

    input {
      font-size: 1.1rem;
      border: none;

      &[type='text'] {
        padding: 0 0.7rem;
        background: #eee;
        width: auto;
      }

      &[type='submit'] {
        background: #595;
        color: #fff;
      }
    }
  }
</style>

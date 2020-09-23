<template>
  <header>
    <h1>{{ title }}</h1>
  </header>
</template>

<script>
  export default {
    name: 'Header',
    props: ['title'],
  };
</script>

<style lang="scss" scoped>
  ::selection {
    background: #fff;
    color: #000;
  }

  header {
    text-align: center;
    background: #000;
    padding: 1rem 0;
    color: white;

    h1 {
      letter-spacing: 3px;
      font-size: 1.6rem;

      @media screen and (min-width: 450px) {
        font-size: 2rem;
      }
    }
  }
</style>

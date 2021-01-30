<template>
  <a class="btn btn-quote">
    {{ name }}
  </a>
</template>

<script>
  export default {
    name: 'button',
    props: ['name'],
  };
</script>

<style scoped>
  
  .btn-quote {
    background-color: var(--current-color);
    color: white;
  }
</style>

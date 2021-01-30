<template>
  <a class="btn-icon" :href="link" target="_blank" rel="noopener noreferrer">
    <slot />
  </a>
</template>

<script>
  export default {
    props: ['link'],
  };
</script>

<style scoped></style>

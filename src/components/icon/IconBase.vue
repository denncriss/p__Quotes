<template>
  <svg
    :viewBox="viewBox"
    viewBox="0 0 28 22"
    fill="currentColor"
    xmlns="http://www.w3.org/2000/svg"
  >
    <slot />
  </svg>
</template>

<script>
  export default {
    props: {
      viewBox: {
        type: String,
        default: '0 0 24 24',
      },
    },
  };
</script>

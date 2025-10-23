<template>
  <button class="btn">
    <slot></slot>
  </button>
</template>

<script>
export default {
  name: 'my-button',
}
</script>

<style scoped>
.btn
{
  padding: 10px 10px;
  background: none;
  color: salmon;
  border: 3px solid salmon;
}
</style>
<template>
  <button class="button">
      <slot></slot>
  </button>
</template>

<script>
export default {
 name: 'my-button'
}
</script>

<style scope>

.button {
  color: rgb(120, 201, 120);
  padding: 10px;
  background-color: #fff;
  border: 1px solid rgb(120, 201, 120);
  cursor: pointer;
}

</style>
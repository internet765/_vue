<template>
  <input :value="value" @input="updateInput" class="input" type="text" />
</template>

<script>
export default {
  name: "my-input",
  props: {
    value: [String, Number],
  },
  methods: {
    updateInput(e) {
      this.$emit("update:value", e.target.value);
    },
  },
};
</script>

<style>
.input {
  width: 100%;
  border: 1px solid rgb(120, 201, 120);
  padding: 5px;
  margin-bottom: 10px;
}
</style>
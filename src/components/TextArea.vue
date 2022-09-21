<template>
  <div class="form-floating">
    <textarea
      class="form-control"
      placeholder="Leave Notes here"
      style="height: 100px"
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
      v-bind="$attrs"
    ></textarea>
    <label>{{ label }}</label>
  </div>
</template>

<script>
export default { props: ["label", "modelValue"] };
</script>

<style></style>

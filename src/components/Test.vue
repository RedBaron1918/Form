<template>
  <div>
    <label class="form-label">{{ label }}</label>
    <input
      type="text"
      class="form-control"
      :value="modelValue"
      @input="$emit('update:modelValue', $event.target.value)"
      v-bind="$attrs"
    />
  </div>
</template>

<script>
export default { props: ["label", "modelValue"] };
</script>

<style></style>

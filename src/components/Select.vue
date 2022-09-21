<template>
  <label class="form-label">{{ label }}</label>
  <select
    class="form-select"
    :value="modelValue"
    @change="$emit('update:modelValue', $event.target.value)"
  >
    <option selected disabled value="">Choose...</option>
    <option value="male">Male</option>
    <option value="female">female</option>
  </select>
</template>

<script>
export default {
  props: ["label", "modelValue"],
};
</script>

<style></style>

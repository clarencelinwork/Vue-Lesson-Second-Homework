<script setup>
defineProps({
  labelName: String,
  placeholder: String
})
</script>

<template>
  <label class="formControls_label" for="pwd">{{ labelName }}</label>
  <input
    class="formControls_input"
    type="password"
    name="pwd"
    id="pwd"
    :placeholder="placeholder"
    required
  />
</template>

<style scoped>

</style>

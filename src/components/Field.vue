<script setup>
defineProps({
  type: {
    type: String,
    default: "input",
  },
  name: {
    type: String,
  },
  // Search for dynamic components : for "as" type
  as: {
    type: String,
  },
  onChange: {
    type: Function,
  },
  updateValue: {
    type: Function,
  },
});
</script>

<template>
  <input :name="name" type="text" v-on:change="onChange" />
</template>

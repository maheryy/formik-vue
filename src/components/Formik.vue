<script setup>
import { reactive } from "vue";

defineProps({
  initialValues: {
    type: Object,
  },
  onSubmit: {
    type: Function,
  },
  validate: {
    type: Function,
  },
});

const data = reactive({});

const handleChange = (name, value) => {
  console.logo(name, value);
};
</script>

<template>
  <form @submit.prevent="onSubmit">
    <slot :handle-change="handleChange"></slot>
  </form>
</template>

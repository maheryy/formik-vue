<script setup>
import { provide, reactive } from "vue";

const {initialValues, onSubmit, validate} = defineProps({
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

const data = reactive({
  values: initialValues,
});

const updateValue = (key, value) => {
  data.values[key] = value;
}

provide("update", updateValue);
</script>

<template>
  <form @submit.prevent="onSubmit(data)">
    <slot></slot>
  </form>
</template>

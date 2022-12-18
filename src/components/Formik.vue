<script setup>
import { provide, reactive, ref, readonly } from "vue";

const { initialValues, onSubmit, validate } = defineProps({
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

const values = reactive(initialValues);
const errors = ref({});
const isSubmitting = ref(false);

const updateValue = (key, value) => {
  values[key] = value;
};

const handleSubmit = async () => {
  isSubmitting.value = true;
  errors.value = await validate(values);

  if (Object.keys(errors.value).length) {
    isSubmitting.value = false;
    return;
  }

  await onSubmit(values);
  isSubmitting.value = false;
};

provide("update", updateValue);
provide("initialValues", readonly(initialValues));
provide("errors", readonly(errors));
</script>

<template>
  <form @submit.prevent="handleSubmit">
    <slot></slot>
  </form>
</template>

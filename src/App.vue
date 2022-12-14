<script setup>
import Field from './components/Field.vue';
import Form from './components/Form.vue';
import Formik from './components/Formik.vue'

const initialValues = {
  "input-1": "",
  "input-2": "",
  "input-3": "",
  "input-4": "",
}
const handleSubmit = (form) => {
  console.log('submit', form);
}

</script>

<template>
  <main>
    <Formik :initialValues="initialValues" :onSubmit="handleSubmit">
      <Field name="input-1"/>
      <Field name="input-2"/>
      <Field name="input-3"/>
      <Field name="input-4"/>
      <button>
        ok
      </button>
    </Formik>
  </main>
</template>

<style scoped></style>

<script setup>
import Field from './components/Field.vue';
import Form from './components/Form.vue';
import Formik from './components/Formik.vue'

const initialValues = {}
const handleSubmit = (e) => {
  console.log('submit');
}

</script>

<template>
  <main>
    <Formik :initial-values="initialValues" :on-submit="handleSubmit">
      <div>
        ok
      </div>
      <button>
        ok
      </button>
    </Formik>
  </main>
</template>

<style scoped></style>

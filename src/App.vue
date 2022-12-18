<script setup>
import Field from "./components/Field.vue";
import Formik from "./components/Formik.vue";

const initialValues = {
  name: "",
  age: "",
  lang: "fr",
  about: "Lorem ipsum dolor sit amet, consectetur adipiscing elit",
};

const handleSubmit = (values) => {
  console.log("submit", values);
};

const validate = (values) => {
  const errors = {};

  if (!values["name"]) {
    errors["name"] = "Name field is required";
  }
  if (values["age"] < 18) {
    errors["age"] = "You must be at least 18 years old";
  }

  return errors;
};
</script>

<template>
  <main>
    <Formik
      :initialValues="initialValues"
      :onSubmit="handleSubmit"
      :validate="validate"
    >
      <Field name="name" placeholder="Name"/>
      <Field name="age" type="number" placeholder="Age"/>
      <Field name="lang" as="select">
        <option value="" disabled>Select your language</option>
        <option value="en">English</option>
        <option value="fr">French</option>
        <option value="es">Spanish</option>
      </Field>
      <Field name="about" as="textarea" placeholder="Tell me about you..."/>
      <button>Submit</button>
    </Formik>
  </main>
</template>

<style scoped></style>

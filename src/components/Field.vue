<script>
export default {
  inheritAttrs: false,
};
</script>

<script setup>
import { inject } from "vue";

const { name, as } = defineProps({
  name: {
    type: String,
  },
  as: {
    type: String,
  },
});

const update = inject("update");
const initialValues = inject("initialValues");
const errors = inject("errors");
</script>

<template>
  <div class="field">
    <component
      :name="name"
      :value="initialValues[name]"
      :is="as || 'input'"
      v-bind="$attrs"
      @change="update(name, $event.target.value)"
    >
      <slot></slot>
    </component>
    <span class="error" v-if="errors[name]">
      {{ errors[name] }}
    </span>
  </div>
</template>

<style scoped>
.field {
  padding: 0.25em 0;
  display: flex;
  flex-direction: column;
}
</style>

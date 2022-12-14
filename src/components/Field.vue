<script setup>
import { inject } from 'vue';

const {name} = defineProps({

  name: {
    type: String,
  },
  // Search for dynamic components : for "as" type
  as: {
    type: String,
  },
});

const update = inject('update');


</script>

<template>
  <input :name="name" type="text" @keydown="update(name, $event.target.value)" />
</template>

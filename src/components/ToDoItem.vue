<template>
  <div>
    <input type="checkbox" :checked="isDone"/>
    <label>{{ label }}</label>
  </div>
</template>

<script setup>
  import { defineProps } from 'vue';

  // Define props directly
  const props = defineProps({
    label: {
      type: String,
      required: true
    },
    isDone: {
        type: Boolean,
        default: false,
        id: "todo-" + crypto.randomUUID(),
    }
  });
</script>

<style scoped>
  /* Your component-specific styles here */
</style>
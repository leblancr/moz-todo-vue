<script setup>
  import { computed } from 'vue';

  // Define props directly
  // destructures the props object into individual variables label, done
  // defineProps is used to define the props that the component expects
  // to receive from its parent. It specifies the type, default values,
  // and whether each prop is required.
  const { label, done } = defineProps({
    label: {
      type: String,
      required: true
    },
    done: {
        type: Boolean,
        default: false
    },
    id: {
      required: true,
      type: String
    },
  });

// Generate a unique ID dynamically
const uniqueId = computed(() => "todo-" + crypto.randomUUID());
</script>

// : means make reactive
// shorthand for the v-bind property, a colon
// v-bind: This directive is used to bind a value
// to an HTML attribute dynamically.
<template>
  <div>
    <input type="checkbox" :checked="done" :id="uniqueId"/>
    <label>{{ label }}</label>
  </div>
</template>

<style scoped>
  /* Your component-specific styles here */
</style>
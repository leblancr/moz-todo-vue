<script setup>
  import { ref } from 'vue';

  const emit = defineEmits(['todo-added']); // Declare the event
  const label = ref(''); // Reactive state for the input

  const onSubmit = () => {
    if (label.value === "") {
      return;
    }
    emit("todo-added", label.value); // emit string to parent
    label.value = ''; // Clear the input field after submission
  };
</script>

<template>
  <form @submit.prevent="onSubmit">
    <label for="new-todo-input"> What needs to be done? </label>
    <input
      type="text"
      id="new-todo-input"
      name="new-todo"
      autocomplete="off"
      v-model.lazy.trim="label" />
    <button type="submit">Add</button>
  </form>
</template>

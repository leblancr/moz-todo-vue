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
    <input
      type="text"
      id="new-todo-input"
      name="new-todo"
      autocomplete="off"
      v-model.lazy.trim="label"
      class="input__lg"/>
    <button class="btn btn__primary btn__lg" type="submit">Add</button>
  </form>
</template>

<style scoped>
.input__lg {
  background-color: gray; /* Light grey background color */
  border: 1px solid #ccc; /* Border color matching the design */
  padding: 0.5rem; /* Add some padding */
  border-radius: 4px; /* Rounded corners */
  font-size: 2rem; /* Adjust font size as needed */
}
</style>
<script setup>
  import { ref } from 'vue';
  import ToDoItem from "./components/ToDoItem.vue";
  import ToDoForm from "./components/ToDoForm.vue";

  const toDoItems = ref([
    { label: 'Learn Vue', done: false },
    { label: 'Create a Vue project with the CLI', done: true },
    { label: 'Have fun', done: true },
    { label: 'Create a to-do list', done: false }
  ]);

  const addToDo = (toDoLabel) => {
    console.log('To-do added:', toDoLabel.value)

    const newToDo = {
      label: toDoLabel, // Set the label from the function parameter
      done: false // Default the new item as not done
    };

    toDoItems.value.push(newToDo);
    console.log(toDoItems.value);
  };
</script>

// v-model is used with done because it represents a dynamic state that needs two-way binding.
// label is a static prop, so it doesn’t require two-way binding.
// @todo-added="addToDo" means listen for the string 'todo-added' call addToDo()
// props go to ToDoItem here
<template>
  <div id="app">
    <h1>To-Do List</h1>
    <ToDoForm @todo-added="addToDo"/>
    <ul>
      <li v-for="(item, index) in toDoItems" :key="index">
        <ToDoItem
          v-model:done="item.done"
          :label="item.label"
          :id="String(index)"
        />
      </li>
    </ul>
  </div>
</template>

<style>
  /* Apply global styles for dark mode */
  html, body {
    margin: 0;
    padding: 0;
    height: 100%;
    background-color: black; /* Dark background color */
    color: #fff; /* White text color */
    font-family: Arial, sans-serif;
  }

  #app {
    min-height: 100vh;
    display: flex;
    flex-direction: column;
    padding: 1rem;
  }

  h1 {
    color: #fff; /* Ensure headings are also white */
  }

  /* Scoped styles */
  header {
    line-height: 1.5;
  }

  @media (min-width: 1024px) {
    header {
      display: flex;
      place-items: center;
      padding-right: calc(var(--section-gap) / 2);
    }

    header .wrapper {
      display: flex;
      place-items: flex-start;
      flex-wrap: wrap;
    }
  }
</style>
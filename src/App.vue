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

// toDoLabel is emitted up from ToDoForm
const addToDo = (toDoLabel) => {
    console.log('To-do added:', toDoLabel.value)

    // make new object and push to toDoItems array
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
    <ul class="stack-small">
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
  /* Global styles */
  .btn {
    padding: 0.8rem 1rem 0.7rem;
    border: 0.2rem solid #4d4d4d;
    cursor: pointer;
    text-transform: capitalize;
    border-radius: 9px; /* Rounded corners */
  }
  .btn__danger {
    color: #fff;
    background-color: #ca3c3c;
    border-color: #bd2130;
  }
  .btn__filter {
    border-color: lightgrey;
  }
  .btn__danger:focus {
    outline-color: #c82333;
  }
  .btn__primary {
    color: #fff;
    background-color: #000;
  }
  .btn-group {
    display: flex;
    justify-content: space-between;
  }
  .btn-group > * {
    flex: 1 1 auto;
  }
  .btn-group > * + * {
    margin-left: 0.8rem;
  }
  .label-wrapper {
    margin: 0;
    flex: 0 0 100%;
    text-align: center;
  }
  [class*="__lg"] {
    display: inline-block;
    width: 100%;
    font-size: 1.9rem;
  }
  [class*="__lg"]:not(:last-child) {
    margin-bottom: 1rem;
  }
  @media screen and (min-width: 620px) {
    [class*="__lg"] {
      font-size: 2.4rem;
    }
  }
  .visually-hidden {
    position: absolute;
    height: 1px;
    width: 1px;
    overflow: hidden;
    clip: rect(1px 1px 1px 1px);
    clip: rect(1px, 1px, 1px, 1px);
    clip-path: rect(1px, 1px, 1px, 1px);
    white-space: nowrap;
  }
  [class*="stack"] > * {
    margin-top: 0;
    margin-bottom: 0;
  }
  .stack-small > * + * {
    margin-top: 1.25rem;
  }
  .stack-large > * + * {
    margin-top: 2.5rem;
  }
  @media screen and (min-width: 550px) {
    .stack-small > * + * {
      margin-top: 1.4rem;
    }
    .stack-large > * + * {
      margin-top: 2.8rem;
    }
  }
  /* End global styles */
  #app {
    background: black;
    margin: 2rem 0 4rem 0;
    padding: 1rem;
    padding-top: 0;
    position: relative;
    box-shadow:
      0 2px 4px 0 rgb(0 0 0 / 20%),
      0 2.5rem 5rem 0 rgb(0 0 0 / 10%);
  }
  @media screen and (min-width: 550px) {
    #app {
      padding: 4rem;
    }
  }
  #app > * {
    max-width: 50rem;
    margin-left: auto;
    margin-right: auto;
  }
  #app > form {
    max-width: 100%;
  }
  #app h1 {
    display: block;
    min-width: 100%;
    width: 100%;
    text-align: center;
    margin: 0;
    margin-bottom: 1rem;
  }
</style>
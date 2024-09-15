<script setup>
  import ToDoItem from "./components/ToDoItem.vue";
</script>

<template>
  <div id="app">
    <h1>To-Do List</h1>
    <ul>
      <li>
        <ToDoItem label="My ToDo Item" :isDone="true"/>
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

  .logo {
    display: block;
    margin: 0 auto 2rem;
  }

  @media (min-width: 1024px) {
    header {
      display: flex;
      place-items: center;
      padding-right: calc(var(--section-gap) / 2);
    }

    .logo {
      margin: 0 2rem 0 0;
    }

    header .wrapper {
      display: flex;
      place-items: flex-start;
      flex-wrap: wrap;
    }
  }
</style>
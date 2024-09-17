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
  <div class="custom-checkbox">
    <input class="checkbox" type="checkbox" :checked="done" :id="uniqueId"/>
    <label :for="uniqueId" class="checkbox-label">{{ label }}</label>
  </div>
</template>

<style scoped>
  .custom-checkbox > .checkbox-label {
    font-family: Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    font-weight: 400;
    font-size: 16px;
    font-size: 1rem;
    line-height: 1.25;
    color: gray;
    display: block;
    margin-bottom: 5px;
  }
  .custom-checkbox > .checkbox {
    font-family: Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    font-weight: 400;
    font-size: 16px;
    font-size: 1rem;
    line-height: 1.25;
    box-sizing: border-box;
    width: 100%;
    height: 40px;
    height: 2.5rem;
    margin-top: 0;
    padding: 5px;
    border: 2px solid #0b0c0c;
    border-radius: 0;
    appearance: none;
  }
  .custom-checkbox > input:focus {
    outline: 2px dashed #fd0;
    outline-offset: 0;
    box-shadow: inset 0 0 0 2px;
  }
  .custom-checkbox {
    font-family: Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    font-weight: 400;
    font-size: 1.6rem;
    line-height: 1.25;
    display: block;
    position: relative;
    min-height: 40px;
    margin-bottom: 10px;
    padding-left: 40px;
    clear: left;
  }
  .custom-checkbox > input[type="checkbox"] {
    -webkit-font-smoothing: antialiased;
    cursor: pointer;
    position: absolute;
    z-index: 1;
    top: -2px;
    left: -2px;
    width: 44px;
    height: 44px;
    margin: 0;
    opacity: 0;
  }
  .custom-checkbox > .checkbox-label {
    font-size: inherit;
    font-family: inherit;
    line-height: inherit;
    display: inline-block;
    margin-bottom: 0;
    padding: 8px 15px 5px;
    cursor: pointer;
    touch-action: manipulation;
  }
  .custom-checkbox > label::before {
    content: "";
    box-sizing: border-box;
    position: absolute;
    top: 0;
    left: 0;
    width: 40px;
    height: 40px;
    border: 2px solid currentcolor;
    background: transparent;
  }
  .custom-checkbox > input[type="checkbox"]:focus + label::before {
    border-width: 4px;
    outline: 2px dashed #228bec;
  }
  .custom-checkbox > label::after {
    box-sizing: content-box;
    content: "";
    position: absolute;
    top: 11px;
    left: 9px;
    width: 18px;
    height: 7px;
    transform: rotate(-45deg);
    border: solid;
    border-width: 0 0 5px 5px;
    border-top-color: transparent;
    opacity: 0;
    background: transparent;
  }
  .custom-checkbox > input[type="checkbox"]:checked + label::after {
    opacity: 1;
  }
  @media only screen and (min-width: 40rem) {
    label,
    input,
    .custom-checkbox {
      font-size: 19px;
      font-size: 1.9rem;
      line-height: 1.31579;
    }
  }
</style>

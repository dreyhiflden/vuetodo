<template>
  <div class="input_container">
    <input class="input" type="text" placeholder="Enter todo text">
    <input class="input" type="text" placeholder="Enter todo description">
    <button class="button">Add task</button>
  </div>
</template>

<script>
  export default {
    name: "TodoInput"
  }
</script>

<style scoped>
  .input_container {
    display: flex;
    flex-direction: row;
    justify-content: space-around;
  }

  .input {
    padding: 5px 10px;
    border-radius: 3px;
    border: 0;
  }

  .input:focus {
    outline: none;
  }

  .button {
    border-radius: 3px;
    border: 0;
    padding: 5px 10px;
    box-shadow: 0 8px 16px 0 rgba(0, 0, 0, 0.2), 0 6px 20px 0 rgba(0, 0, 0, 0.19);
    transition: box-shadow ease-in-out 0.3s;
  }

  .button:hover {
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 3px 10px 0 rgba(0, 0, 0, 0.19);
  }

  .button:active {
    background: linear-gradient(to bottom, #afd48e 0%,#86c050 100%);
    color: #fff;
  }

  .button:focus {
    outline: none;
  }
</style>
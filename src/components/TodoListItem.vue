<template>
  <li class="todo-list__item">
    {{ todo.text }}<br>
    {{ todo.descr }}
    <button @click="$emit('remove', todo.id)">
      X
    </button>
  </li>
</template>

<script>
  export default {
    props: {
      todo: {
        type: Object,
        required: true
      }
    }
  }
</script>

<style>
  .todo-list__item {
    list-style: none;
    padding: 0;
  }
</style>
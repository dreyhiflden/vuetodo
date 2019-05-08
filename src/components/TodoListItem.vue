<template>
  <li class="todo-list__item" @mouseover="isHovered = true" @mouseleave="isHovered = true">
    <div class="item-content">
      <p v-if="!isEditing" class="todo-text">{{ todo.text }}</p>
      <input class="editing-input editing-input--title"
             v-if="isEditing"
             maxlength="30"
             v-model="todo.text"
             type="text">
      <p v-if="!isEditing" class="todo-descr">{{ todo.descr }}</p>
      <input class="editing-input editing-input--subtitle"
             v-if="isEditing"
             maxlength="60"
             v-model="todo.descr"
             type="text">
    </div>
    <div v-show="isHovered" class="hover-details">
      <div class="hover-details__item">
        <button class="btn btn--red" @click="$emit('remove', todo.id)">Delete</button>
      </div>
      <div class="hover-details__item">
          <button class="btn btn--green" @click="isEditing = !isEditing">
            {{ isEditing ? 'Save' : 'Edit' }}
          </button>
      </div>
    </div>
  </li>
</template>

<script>
  export default {
    props: {
      todo: {
        type: Object,
        required: true
      },
    },
    data: function() {
      return {
        isHovered: false,
        isEditing: false,
      }
    },
  }
</script>

<style>
  .todo-list__item {
    list-style: none;
    padding: 10px 0 10px 20px;
    margin: 0 0 20px 0;
    border-radius: 5px;
    border-bottom: 1px solid rgba(255, 255, 255, 0.02);
    display: flex;
    justify-content: space-between;
    height: 60px;
  }

  .todo-list__item:hover {
    background: linear-gradient(135deg, #ffffff14 0%, #ffffff03 23%, #ffffff08 100%);
  }

  .todo-text {
    margin: 0;
    font-size: 21px;
    font-weight: bold;
    line-height: 1.33;
  }

  .todo-descr {
    margin: 0;
    font-size: 14px;
    color: rgba(255, 255, 255, 0.41);
    line-height: 1.33;
  }

  .hover-details {
    width: 120px;
    display: flex;
    flex-direction: column;
    justify-content: space-around;
    position: relative;
  }

  .hover-details::before {
    content: '';
    position: absolute;
    top: -10px;
    left: 0;
    background: rgba(255, 255, 255, 0.02);
    width: 1px;
    height: 80px;
  }

  .hover-details__item {
    display: flex;
    justify-content: center;
    align-items: center;
    align-content: center;
    height: 200px;
    padding: 7px 0 8px 0;
  }

  .hover-details__item:first-child {
    margin: 0 0 0 0;
    border-top-right-radius: 5px;
    border-bottom: 1px solid rgba(255, 255, 255, 0.02);
  }

  .hover-details__item:hover {
    background: rgba(255, 255, 255, 0.02);
  }

  .btn {
    background: none;
    padding: 5px;
    margin: 0;
    border: none;
    color: #fff;
    font-weight: bold;
  }

  .btn--green {
    color: #9DC876;
  }

  .btn--red {
    color: #DF5C5E;
  }

  .item-content {
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  .editing-input {
    padding: 2px;
    border: 0;
    width: 455px;
    background: rgba(0, 0, 0, 0.05);
  }

  .editing-input--title {
    color: #fff;
    font-size: 21px;
    font-weight: bold;
    font-style: italic;
  }

  .editing-input--subtitle {
    color: rgba(255, 255, 255, 0.41);
    font-size: 14px;
    font-style: italic;
  }

  .fade-enter-active, .fade-leave-active {
    transition: opacity .5s;
  }
  .fade-enter, .fade-leave-to /* .fade-leave-active below version 2.1.8 */ {
    opacity: 0;
  }
</style>
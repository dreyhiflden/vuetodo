<template>
  <li class="todo-list__item" @mouseover="isHovered = true" @mouseleave="isHovered = false">
    <div class="todo-list__container">
      <p v-if="!isEditing" class="todo-list__title">{{ todo.text }}</p>
      <input class="editing-input editing-input--title"
             v-if="isEditing"
             maxlength="30"
             v-model="todo.text"
             type="text">
      <p v-if="!isEditing" class="todo-list__description">{{ todo.description }}</p>
      <input class="editing-input editing-input--description"
             v-if="isEditing"
             maxlength="60"
             v-model="todo.description"
             type="text">
    </div>
    <div v-show="isHovered" class="hover-details">
      <div class="hover-details__item">
        <button class="hover-details__button hover-details__button--red" @click="$emit('remove', todo.id)">Delete</button>
      </div>
      <div class="hover-details__item">
        <button class="hover-details__button hover-details__button--green" @click="blur" v-if="!isEditing">
          Edit
        </button>
        <button class="hover-details__button hover-details__button--green" @click="unblur" v-if="isEditing">
          Save
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
    methods: {
      blur(e) {
        let currentTodoItem = e.currentTarget.parentNode.parentNode.parentNode;
        let todoItemsCollection = document.querySelectorAll('.todo-list__item');
        let todoItemsArray = Array.prototype.slice.call(todoItemsCollection);
        let currentTodoItemIndex = todoItemsArray.indexOf(currentTodoItem);
        for (let i = 0; i < todoItemsCollection.length; i++) {
          if (i !== currentTodoItemIndex) {
            todoItemsCollection[i].style.filter = "blur(4px)"
          }
        }
        this.isEditing = true;
      },
      unblur(e) {
        let currentTodoItem = e.currentTarget.parentNode.parentNode.parentNode;
        let todoItemsCollection = document.querySelectorAll('.todo-list__item');
        let todoItemsArray = Array.prototype.slice.call(todoItemsCollection);
        let currentTodoItemIndex = todoItemsArray.indexOf(currentTodoItem);
        for (let i = 0; i < todoItemsCollection.length; i++) {
          if (i !== currentTodoItemIndex) {
            todoItemsCollection[i].style.filter = "none"
          }
        }
        this.isEditing = false;
      }
    },
  }
</script>

<style scoped>
  .todo-list__item {
    list-style: none;
    padding: 10px 0 10px 20px;
    margin: 0 0 20px 0;
    border-radius: 5px;
    border-bottom: 1px solid rgba(255, 255, 255, 0.02);
    display: flex;
    justify-content: space-between;
    height: 60px;
    transition: all ease 0.1s;
  }

  .todo-list__item:hover {
    background: linear-gradient(135deg, #ffffff14 0%, #ffffff03 23%, #ffffff08 100%);
  }

  .todo-list__title {
    margin: 0;
    font-size: 21px;
    font-weight: bold;
    line-height: 1.33;
  }

  .todo-list__description {
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
    padding: 1px 0 0 0;
  }

  .hover-details__item:first-child {
    margin: 0;
    border-top-right-radius: 5px;
    border-bottom: 1px solid rgba(255, 255, 255, 0.02);
  }

  .hover-details__item:hover {
    background: rgba(255, 255, 255, 0.02);
  }

  .hover-details__button {
    background: none;
    padding: 5px;
    margin: 0;
    border: none;
    color: #fff;
    font-weight: bold;
    height: 38px;
    width: 118px;
    outline: none;
  }

  .hover-details__button:active {
    background: rgba(255, 255, 255, 0.05);
  }

  .hover-details__button--green {
    color: #9DC876;
  }

  .hover-details__button--red {
    color: #DF5C5E;
  }

  .todo-list__container {
    display: flex;
    flex-direction: column;
    justify-content: center;
  }

  .editing-input {
    border: 0;
    width: 455px;
    background: transparent;
    outline: none;
  }

  .editing-input--title {
    color: #fff;
    font-size: 21px;
    font-weight: bold;
    font-style: italic;
  }

  .editing-input--description {
    font-size: 14px;
    font-style: italic;
    color: rgba(255, 255, 255, 0.41);
  }
</style>

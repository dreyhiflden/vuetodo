<template>
  <div class="input-form">
    <div class="input-form__container">
      <div class="inputs">
        <input class="input input--title"
               v-model="newTodoTitle"
               type="text"
               maxlength="30"
               placeholder="Enter todo text">
        <input class="input input--subtitle"
               v-model="newTodoDescription"
               type="text"
               maxlength="60"
               placeholder="Enter todo description">
      </div>
      <button class="add-todo-button" @click="addItem" :disabled="isNotEmpty">
        +
      </button>
    </div>
  </div>
</template>

<script>
  export default {
    data: function() {
      return {
        newTodoTitle: null,
        newTodoDescription: null,
      }
    },
    methods: {
      addItem () {
        let inputData = {
          text: this.newTodoTitle,
          description: this.newTodoDescription,
        };

        this.$emit('addItem', inputData);
        this.newTodoTitle = '';
        this.newTodoDescription = '';
      },
    },
    computed: {
      isNotEmpty() {
        return this.newTodoTitle === null || this.newTodoTitle.length < 1;
      }
    }
  }
</script>

<style scoped>
  .input-form {
    position: relative;
  }

  .input-form__container {
    display: flex;
    align-items: center;
    justify-content: center;
    margin: 40px 0 40px 0;
    padding: 0 20px;
  }

  .input {
    padding: 10px 10px;
    border-radius: 3px;
    border: 0;
    transition: width 0.5s;
    color: rgb(255, 255, 255);
    background: rgba(0, 0, 0, 0.15);
    box-sizing: border-box;
  }

  .input--title {
    width: 220px;
    margin: 0 0 10px 0;
  }

  .input--subtitle {
    width: 220px;
  }

  .input:focus {
    outline: none;
  }

  .inputs {
    display: flex;
    flex-direction: column;
  }

  .add-todo-button {
    position: relative;
    border-radius: 50%;
    text-shadow: #9DC876 0 0 4px;
    font-size: 42px;
    line-height: 1.33;
    border: 10px solid #535668;
    height: 90px;
    color: #9DC876;
    width: 90px;
    background: radial-gradient(ellipse at center, #404150 0%,#363642 80%);
    margin: 0 0 0 -30px;
    padding: 5px 10px;
    box-shadow: 0 4px 8px 0 rgba(0, 0, 0, 0.2), 0 3px 10px 0 rgba(0, 0, 0, 0.19);
    transition: all ease-in-out 0.3s;
  }

  .add-todo-button:disabled {
    color: #727588;
    text-shadow: none;
  }

  .add-todo-button:hover {
    box-shadow: 0 8px 12px 0 rgba(0, 0, 0, 0.2), 0 6px 15px 0 rgba(0, 0, 0, 0.19);
  }

  .add-todo-button:active {
    background: radial-gradient(ellipse at center, #454655 0%, #3b3b48 80%);
  }

  .add-todo-button:focus {
    outline: none;
  }
</style>

<template>
  <div class="input-form">
    <div class="input_container">
      <input class="input input--title"
             v-model="newTodoTitle"
             type="text"
             maxlength="30"
             @focus="focused" @blur="blur"
             placeholder="Enter todo text">
      <input class="input input--subtitle"
             v-model="newTodoDescription"
             type="text"
             @focus="focused" @blur="blur"
             maxlength="60"
             placeholder="Enter todo description">
<!--      <button class="button" @click="addItem" :disabled="newTodoTitle === null || newTodoTitle.length < 1">Create-->
<!--        task</button>-->
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
          descr: this.newTodoDescription,
        };

        this.$emit('addItem', inputData);
        this.newTodoTitle = '';
        this.newTodoDescription = '';
      },
      blur(e) {
        e.currentTarget.style.width = "255px";
      },
      focused(e) {
        e.currentTarget.style.width = "255px";
      }
    },
  }
</script>

<style scoped>
  .input-form {
    position: relative;
  }

  .input-form::after {
    content: '';
    position: absolute;
    top: 0;
    left: 620px;
    right: -20px;
    bottom: 0;
    width: 10px;
    height: 10px;
    background: red;
  }

  .input_container {
    display: grid;
    grid-template-columns: 50% 50%;
    grid-gap: 20px;
    margin: 40px 0 40px 0;
    padding: 0 20px;
  }

  .input {
    padding: 5px 10px;
    border-radius: 3px;
    border: 0;
    transition: width 0.5s;
    color: rgb(255, 255, 255);
    background: rgba(0, 0, 0, 0.15);
  }

  .input--title {
    width: 255px;
    /*width: 190px;*/
  }

  .input--subtitle {
    width: 255px;
    /*width: 190px;*/
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
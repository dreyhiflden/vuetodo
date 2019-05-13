<template>
  <div>
    <AddTaskForm @addItem="addTodo" />
    <ul v-if="todos.length" class="todo-list">
      <transition-group name="list" tag="div" id="todolist">
        <TodoListItem
          v-for="todo in todos"
          :key="todo.id"
          :todo="todo"
          class="list-item"
          @remove="removeTodo"
        />
      </transition-group>
    </ul>
    <p v-else class="empty-list">
      Nothing left in the list. Add a new todo in the input above.
    </p>
  </div>
</template>

<script>
  import TodoListItem from './TodoListItem.vue'
  import AddTaskForm from './AddTaskForm.vue'

  let nextTodoId = 1;

  export default {
    components: {
      TodoListItem,
      AddTaskForm,
    },
    data() {
      return {
        todos: [
          {
            id: nextTodoId++,
            text: 'Learn Vue',
            description: 'First item description'
          },
          {
            id: nextTodoId++,
            text: 'Learn about single-file components',
            description: 'Second item description'
          },
          {
            id: nextTodoId++,
            text: 'Fall in love',
            description: 'Third item description'
          }
        ]
      }
    },
    methods: {
      addTodo(inputData) {
        this.todos.push({
          id: nextTodoId++,
          text: inputData.text,
          description: inputData.description,
        });
      },
      removeTodo(idToRemove) {
        this.todos = this.todos.filter(todo => {
          return todo.id !== idToRemove
        });
      }
    }
  }
</script>

<style scoped>
  .todo-list {
    padding: 0;
  }

  .empty-list {
    text-align: center;
  }

  .list-enter-active, .list-leave-active {
    transition: all 0.3s;
  }
  .list-enter, .list-leave-to {
    opacity: 0;
    transform: translateY(30px);
  }
</style>

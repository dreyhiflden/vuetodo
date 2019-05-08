<template>
  <div>
    <AddTaskForm @addItem="addTodo" />
    <ul v-if="todos.length" class="todo-list">
      <TodoListItem
        v-for="todo in todos"
        :key="todo.id"
        :todo="todo"
        @remove="removeTodo"
      />
    </ul>
    <p v-else>
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
    data () {
      return {
        todos: [
          {
            id: nextTodoId++,
            text: 'Learn Vue',
            descr: 'First item description'
          },
          {
            id: nextTodoId++,
            text: 'Learn about single-file components',
            descr: 'Second item description'
          },
          {
            id: nextTodoId++,
            text: 'Fall in love',
            descr: 'Third item description'
          }
        ]
      }
    },
    methods: {
      addTodo (inputData) {
        this.todos.push({
          id: nextTodoId++,
          text: inputData.text,
          descr: inputData.descr,
        });
      },
      removeTodo (idToRemove) {
        this.todos = this.todos.filter(todo => {
          return todo.id !== idToRemove
        })
      }
    }
  }
</script>

<style scoped>
  .todo-list {
    padding: 0;
  }
</style>
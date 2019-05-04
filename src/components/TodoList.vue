<template>
  <div>
    <TodoInput />
    <ul v-if="todos.length">
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
  import TodoInput from './TodoInput.vue'

  let nextTodoId = 1;

  export default {
    components: {
      TodoListItem,
      TodoInput,
    },
    data () {
      return {
        newTodoText: '',
        newTodoDescr: '',
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
      addTodo () {
        const trimmedText = this.newTodoText.trim();
        if (trimmedText) {
          this.todos.push({
            id: nextTodoId++,
            text: trimmedText,
            descr: newTodoDescr,
          });
          this.newTodoText = '';
          this.newTodoDescr = '';
        }
      },
      removeTodo (idToRemove) {
        this.todos = this.todos.filter(todo => {
          return todo.id !== idToRemove
        })
      }
    }
  }
</script>
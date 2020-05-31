<template lang="html">
  <div class="todo">
    <div class="filter">
      <select v-model="visibilityFilter">
        <option value="all">all</option>
        <option value="active">active</option>
        <option value="completed">completed</option>
      </select>
    </div>
    <div class="spacer" />
    <table class="todo-list">
      <tr v-for="todo in filteredTodos" :key="todo.id">
        <td :class="{ completed: todo.completed }">
          {{ todo.title }}
        </td>
        <td>
          <button @click="onToggleButtonClick(todo.id)">
            toggle
          </button>
        </td>
        <td>
          <button @click="onDeleteButtonClick(todo.id)">
            delete
          </button>
        </td>
      </tr>
    </table>
    <div class="spacer" />
    <div class="new-todo-form">
      <input type="text" v-model="newTodoTitle" />
      <div class="spacer" />
      <button @click="onNewTodoAddButtonClick">add</button>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      visibilityFilter: 'all',
      todos: [
        {
          id: 1,
          title: "Do the dishes",
          completed: false
        },
        {
          id: 2,
          title: "Take out trash",
          completed: false
        },
        {
          id: 3,
          title: "Finish doing laundry",
          completed: true
        }
      ],
      newTodoTitle: '',
      newId: 4
    }
  },

  computed: {
    filteredTodos() {
      const { visibilityFilter, todos } = this

      switch (visibilityFilter) {
        case 'all':
          return todos
        case 'active':
          return todos.filter(todo => !todo.completed)
        case 'completed':
          return todos.filter(todo => todo.completed)
        default:
          return todos
      }
    }
  },

  methods: {
    onNewTodoAddButtonClick() {
      const { todos, newTodoTitle, newId } = this

      this.todos = [
        ...todos,
        {
          id: newId,
          title: newTodoTitle,
          completed: false
        }
      ]

      this.newId = newId + 1

      this.newTodoTitle = ''
    },

    onToggleButtonClick(id) {
      const { todos } = this

      this.todos = todos.map(todo => (
        todo.id === id
          ? { ...todo, completed: !todo.completed }
          : todo
      ))
    },

    onDeleteButtonClick(id) {
      const { todos } = this

      this.todos = todos.filter(todo => todo.id !== id)
    }
  }
}
</script>

<style lang="css" scoped>
* {
  font-size: 16px;
  outline: none;
}
.spacer {
  display: inline-block;
  width: 10px;
  height: 10px;
}
.completed {
  text-decoration: line-through;
}
</style>

<template>
  <div class="container">
    <Header />
    <AddTodo @addTodo="addTodo" />
    <a-divider />
    <Todos :todos="filtredTodos" @removeTodo="removeTodo" />
    <a-divider />
    <FilterButtons 
      @filterTodo="setFilter"
      :filter="filter"
    />
    <a-divider />
    <div class="delete-all">
      <a-button block type="danger" @click="deleteAll">
        Delete All
      </a-button>
    </div>
  </div>
</template>

<script>
import Header from './Header.vue';
import AddTodo from './AddTodo.vue';
import Todos from './Todos.vue';
import FilterButtons from './FilterButtons.vue';
export default {
  components: {
    Header,
    AddTodo,
    Todos,
    FilterButtons
},
  data() {
    return {
      todos: [],
      filter: "all"
    }
  },
  methods: {
    addTodo(text) {
      if(text.trim()) {
        this.todos.push({
          id: Date.now(),
          title: text,
          isDone: false
        })
      }
    },

    removeTodo(id) {
      this.todos = this.todos.filter(i => i.id !== id)
    },

    deleteAll() {
      this.todos = []
    },

    setFilter(filter) {
      this.filter = filter;
    }
  },
  computed: {
    filtredTodos() {
      if(this.filter === "completed") {
        return this.todos.filter(i => i.isDone)
      }

      if(this.filter === "notCompleted") {
        return this.todos.filter(i => !i.isDone)
      }

      return this.todos
    }
  }
}
</script>

<style scoped>
  .container {
    padding: 0px 0px 10px;
    min-width: 600px;
    max-width: 600px;
    -webkit-box-shadow: 1px 1px 8px 2px rgba(34, 60, 80, 0.27);
    -moz-box-shadow: 1px 1px 8px 2px rgba(34, 60, 80, 0.27);
    box-shadow: 1px 1px 8px 2px rgba(34, 60, 80, 0.27);
  }
  .a-devider {
    margin: 10px 0;
  }

  .delete-all {
    padding: 0 10px;
  }
</style>
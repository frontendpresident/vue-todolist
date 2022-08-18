<template>
  <div class="todos-container">
    <TodoItem
      v-for="todo in todos"
      v-if="todos.length > 0"
      :todo="todo"
      @removeTodo="removeTodo"
    />
    <a-empty v-else />
  </div>
</template>

<script>
import TodoItem from './TodoItem.vue';
export default {
    props: ["todos"],
    components: { TodoItem },
    methods: {
      removeTodo(id) {
        this.$emit("removeTodo", id)
      }
    }
}
</script>

<style>
  .todos-container {
    width: 100%;
    padding: 0 10px;
  }
</style>
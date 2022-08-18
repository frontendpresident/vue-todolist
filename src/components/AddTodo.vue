<template>
  <div class="add-todo-container">
      <a-input placeholder="Add todo..." v-model:value="value" />
      <a-button type="primary" @click="add" >Add todo</a-button>
  </div>
</template>

<script>
export default {
  data() {
    return {
      value: ""
    }
  },
  methods: {
    add() {
      this.$emit('addTodo', this.value)
      this.value = ""
    }
  },
}
</script>

<style>
  .add-todo-container {
    display: flex;
    width: 100%;
    padding: 0 10px;
  }
</style>
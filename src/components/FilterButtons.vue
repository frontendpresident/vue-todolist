<template>
  <div class="filter-container">
    <a-button @click="all">All</a-button>
    <a-button @click="completed">Completed</a-button>
    <a-button @click="notCompleted">Not completed</a-button>
  </div>
</template>

<script>
export default {
  props: ["filter"],
  methods: {
    all() {
      this.$emit("filterTodo", "all")
    },
    completed() {
      this.$emit("filterTodo", "completed")
    },
    notCompleted() {
      this.$emit("filterTodo", "notCompleted")
    }
  }
}
</script>

<style scoped>
  .filter-container {
    width: 100%;
    padding: 0 10px;
    display: flex;
    justify-content: space-between;
    align-items: center;
  }

  button {
    min-width: 150px;
  }
</style>
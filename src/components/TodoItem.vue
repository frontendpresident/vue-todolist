<template>
  <div class="todo-item">
    <h3 
      :class="{ done: todo.isDone }"
      @click="todo.isDone = !todo.isDone"
    >
      {{todo.title}}
    </h3>
    <close-circle-filled class="icon" @click="removeTodo" />
  </div>
</template>

<script>
import CloseCircleFilled from '@ant-design/icons-vue/lib/icons/CloseCircleFilled';
export default {
  props: ["todo"],
  components: {
    CloseCircleFilled
  },
  methods: {
    removeTodo() {
      this.$emit("removeTodo", this.todo.id)
    }
  }
}
</script>

<style scoped>
  .todo-item {
    display: flex;
    justify-content: space-between;
    align-items: center;
    border-bottom: 1px dashed black;
    padding: 0 5px;
    margin-bottom: 10px;
  }

  h3 {
    width: 80%;
    text-align: left;
  }
  
  .icon {
    color: red;
    font-size: 24px;
    cursor: pointer;
  }

  .done {
    text-decoration: line-through;
  }
</style>
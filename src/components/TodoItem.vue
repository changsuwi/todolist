<template>
  <div class="todo-item">
    <input
      class="task-complete-checkbox"
      type="checkbox"
      @change="completeTodo"
    >
    <label class="todo-content">{{ todo.name }}</label>
    <button
      class="btn btn-danger"
      @click="deleteTodo"
    >
      delete
    </button>
  </div>
</template>
<script>
export default {
  props: {
    todo: {
      type: Object,
      default() {
        return {
          name: ''
        }
      }
    }
  },
  emits: ['complete', 'delete'],
  methods: {
    completeTodo() {
      this.$emit("complete")
    },
    deleteTodo() {
      this.$emit("delete")
    },
  },
}
</script>
<style lang="scss" scoped>
.todo-item {
  border-bottom: 1px solid #f0f0f0;
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  margin: 10px;
  align-items: center;
  height: 50px;
}
.todo-content {
  line-height: 21px;
  margin-right: 20px;
  flex-grow: 1;
  text-align: start;
}
.task-complete-checkbox {
  margin-right: 15px;
  transform: scale(1.5);
}
</style>
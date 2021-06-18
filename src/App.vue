<template>
  <div class="project-container">
    <h2 class="project-title">
      {{ projectTitle }}
    </h2>
    <div class="todolist">
      <ul>
        <li v-for="(todo, index) in todolist" :key="todo.id">
          <todo-item
            :todo="todo"
            v-on:complete="completeTodo(index)"
            v-on:delete="deleteTodo(index)"
          />
        </li>
      </ul>
    </div>
    <div class="add-todo-bar">
      <input v-model="taskName" class="add-todo-input" type="text" />
      <button class="btn btn-danger" @click="addTodo">add</button>
    </div>
  </div>
</template>

<script>
import TodoItem from "./components/TodoItem.vue";
export default {
  name: "App",
  components: {
    TodoItem,
  },
  data: () => {
    return {
      projectTitle: "Todo List",
      taskName: "",
      todolist: [],
      id: 0,
    };
  },
  methods: {
    addTodo() {
      if (this.taskName.trim() == "") {
        this.taskName = "";
        return;
      }
      this.todolist.push({
        name: this.taskName,
        id: this.id,
      });
      this.id += 1;
      this.taskName = "";
      console.log("add", this.todolist);
    },
    completeTodo(taskIndex) {
      this.todolist.splice(taskIndex, 1);
      console.log("complete", this.todolist);
    },
    deleteTodo(taskIndex) {
      this.todolist.splice(taskIndex, 1);
      console.log("delete", this.todolist);
    },
  },
};
</script>

<style lang="scss" scoped>
.project-container {
  margin: 0 15px;
  background: #ffffff;
  border-radius: 30px;

  @media (min-width: 768px) {
    margin: 0 40px;
  }
}

.project-title {
  margin-top: 15px;
}

.todolist {
  margin-bottom: 30px;
  min-height: 65vh;
  @media (min-height: 667px) {
    min-height: 70vh;
  }

  @media (min-height: 812px) {
    min-height: 75vh;
  }
}

ul {
  padding: 0;
  list-style-type: none;
}

.add-todo-bar {
  display: flex;
  flex-direction: row;
  justify-content: center;
  margin: 15px;
}
.add-todo-input {
  flex-grow: 1;
  height: 40px;
  font-size: 15px;
  border: 1px solid #dce4ec;
  border-radius: 2em;
  transition: border 250ms ease-out;
  margin: 0px 10px;
  box-sizing: border-box;
  padding-left: 10px;
  max-width: 500px;
}

.add-todo-input:focus {
  border: 1px solid;
  outline: none;
}
</style>

<style lang="scss">
html,
body {
  margin: 0 !important;
  padding: 0 !important;
  background-color: #e2e8f0;
  height: 100%;
}
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}
.btn {
  cursor: pointer;
  font-size: 15px;
  padding: 10px 20px;
  border-radius: 2em;
  background: none;
  border: 1px solid;
  transition: 250ms ease-out;
}

.btn:active {
  color: #fff;
  background: #e74c3c;
}
</style>

<template>
<div class="project-container">
  <div class="project-title">
    <h2>
      {{projectTitle}}
    </h2>
  </div>
  <div class="todolist">
    <ul>
      <li class="todo-item" v-for="(todo, index) in todolist" :key="todo.id">
        <input class="task-complete-checkbox" type="checkbox" @change="complete(index)">
        <label class="todo-content">{{todo.name}}</label>
      </li>
    </ul>
  </div>
  <div class="add-todo-bar">
    <input class="add-todo-input" type="text" v-model="taskName">
    <button @click="addTodo" class="btn btn-danger"> add </button>
  </div>
</div>

</template>

<script>

export default {
  name: 'App',
  data: () => {
    return {
      projectTitle: 'Todo List',
      taskName: '',
      todolist: [],
      id: 0
    } 
  },
  methods: {
    addTodo() {
      this.todolist.push({
        name: this.taskName,
        id : this.id
      })
      this.id += 1
      console.log(this.todolist)
    },
    complete(taskIndex) {
      this.todolist.splice(taskIndex, 1)
      console.log(this.todolist)
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
.project-container {
  margin: 15px;
  background: #ffffff;
}
.todolist {
  margin-bottom: 30px;
  min-height: 70vh;
}
@media (min-height: 667px) {
  .todolist {
    min-height: 75vh;
  }
}

@media (min-height: 812px) {
  .todolist {
    min-height: 80vh;
  }
}

.todo-item {
  border-bottom: 1px solid #f0f0f0;
  display: flex;
  flex-direction: row;
  justify-content: flex-start;
  padding: 10px;
}
.todo-content {
  line-height: 21px;
}
.task-complete-checkbox {
  margin-right: 5px;
}
.add-todo-bar {
  display: flex;
  flex-direction: row;
  justify-content: center;
}
.add-todo-input {
  margin-right: 25px;
  height: 40px;
  font-size: 15px;
  border: 1px solid #dce4ec;
  border-radius: 2em;
  transition: border 250ms ease-out;
  padding: 0px 10px;

}

.add-todo-input:focus {
  border: 1px solid;
  outline: none;
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

.btn:hover {
  color: #fff;
  background: #e74c3c;
}

.btn:focus {
  color: #fff;
  outline: none;
}

</style>

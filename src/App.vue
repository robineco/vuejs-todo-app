<template>
  <div id="app">
    <h1>Vue Todo App</h1>
    <TaskForm @add:task="addNewTask" />
    <ProgressIndicator :progress="this.progress" />
    <ProgressBar :progress="this.progress" />
    <TaskTable :tasks="this.tasks" @remove:task="removeTask" />
  </div>
</template>

<script>
import TaskForm from "./components/TaskForm.vue"
import TaskTable from "./components/TaskTable.vue"
import ProgressIndicator from "./components/ProgressIndicator.vue"
import ProgressBar from "./components/ProgressBar.vue"

export default {
  name: 'App',
  components: {
    TaskForm,
    TaskTable,
    ProgressIndicator,
    ProgressBar,
  },
  data() {
    return {
      tasks: [],
      progress: {
        todo: 0,
        completed: 0,
      }
    }
  },
  methods: {
    addNewTask(task){
      const id = this.tasks.length;
      const name = task.name
      const content = task.content;
      const completed = false;
      const newTask = {id, name, content, completed}

      this.tasks = [...this.tasks, newTask]
      this.progress.todo++;
    },
    removeTask(id) {
      this.tasks = this.tasks.filter(
        task => task.id !== id
      )
      this.progress.todo--;
      this.progress.completed++;
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
</style>

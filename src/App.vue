<template>
  <div class="container">
    <CompProgress :taskProgress="taskList" />
    <CompRegister @taskListEvent="createTasksList" />
    <CompTasks :tasks="taskList"/>
  </div>
</template>

<script>
import CompProgress from './components/CampProgress.vue'
import CompRegister from './components/CompRegister.vue'
import CompTasks from './components/CompTasks.vue'

export default {
  name: 'App',
  components: { CompProgress, CompRegister, CompTasks },
  data() {
    return {
      taskList: [],
    }
  },
  methods: {
    createTasksList(newTask) {
      let sameTaskCheck = this.taskList.find(tsk => tsk.title === newTask)
      if(sameTaskCheck || newTask === '' || newTask === ' ') {
        alert('Nome inválido ou a tarefa ja existe na lista!')
      } else {
        this.taskList.push({title: newTask, complete: false})
      }
    }
  },
  watch: {
    taskList: {
      handler() {
        let stringTasks = JSON.stringify(this.taskList)
        localStorage.setItem('taskList', stringTasks)
      },
      deep: true
    }
  },
  created() {
    let taskJSON = localStorage.getItem('taskList');
    this.taskList = JSON.parse(taskJSON) || [];
  }
}
</script>

<style>
* {
  box-sizing: border-box;
}
html {
  font-family: 'Electrolize', sans-serif;
}
body {
  margin: 0;
  background: linear-gradient(to right, rgb(70, 70, 204), rgb(77, 77, 77) );
}

.container {
  display: grid;
  justify-content: center;
  grid-template-areas: 
    'progress'
    'register'
    'tasks'
  ;
}

</style>

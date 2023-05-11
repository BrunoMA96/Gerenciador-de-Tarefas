<template>
  <div class="progress">
    <h2>Tarefas</h2>
    <div class="progress-bar">
      <div class="progress-text">{{progress}}%</div>
      <div class="progress-color" :style="{width: progress + '%'}">
      </div>
    </div>
  </div>
</template>

<script>
export default {
    name: 'CompProgress',
    props: {
      taskProgress: {
        type: Array,
        required: true
      }
    },
    computed: {
      progress() {
        let allTasks = this.taskProgress.length
        let doneTasks = this.taskProgress.filter(tsk => tsk.complete === true).length
        return Math.round(doneTasks / allTasks * 100) || 0
      }
    }
}
</script>

<style>
.progress {
  grid-area: progress;
  display: flex;
  flex-direction: column;
  justify-content: flex-end;
  align-items: center;
  width: 65vw;
  height: 30vh;
}

.progress-bar {
  position: relative;
  text-align: center;
  margin: 10px 0;
  width: 100%;
  border: 1px solid rgb(39, 39, 39);
  border-radius: 5px;
}

.progress-color {
  position: absolute;
  height: 100%;
  top: 0%;
  border-radius: 5px;
  background: linear-gradient(to right, rgba(0, 173, 0, 0.8), rgba(0, 97, 0, 0.8));
}

.progress-text {
  position: relative;
  color: black;
  padding: 2px 0;
  z-index: 1;
}

.progress-bar div{
  font-weight: bold;
}

@media (max-width: 1024px) and (min-width: 768px) {
  .progress {
    width: 75vw;
  }
}

@media (max-width: 768px){
  .progress {
    width: 100vw;
  }
  .progress-bar {
    width: 95vw;
  }
}

</style>
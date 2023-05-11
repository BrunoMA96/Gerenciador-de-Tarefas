<template>
  <div class="tasks">
    <div class="task-item" v-for="(task, index) in tasks" :key="task.title" :class="task.complete ? 'done' : 'pending'">
        <h2>{{task.title}}</h2>
        <button style="color: green" @click="CompleteTask(task)">&#10004;</button>
        <button style="color: red" @click="DeleteTask(index)">&#10008;</button>
    </div>
  </div>
</template>

<script>

export default {
    name: 'CompTasks',
    props: {
        tasks: {
            type: Array,
            required: true
        }
    },
    methods: {
        DeleteTask(i) {
            let taskArray = this.tasks
            taskArray.splice(i, 1)
        },
        CompleteTask(task) {
            task.complete = !task.complete
        }
    }
}
</script>

<style>
.tasks {
    display: flex;
    flex-direction: column;
    align-items: center;
    grid-area: tasks;
    width: 65vw;
    height: 55vh;
    overflow: auto;
}

.task-item {
    display: inline-flex;
    margin-bottom: 10px;
    width: 100%;
    border: 1px solid rgb(51, 51, 51);
    border-radius: 6px;
}

.task-item:hover {
    box-shadow: 1px 1px 2px rgb(31, 31, 31);
}

.task-item h2 {
    padding: 10px 20px;
    margin: 0 auto;
}

.task-item button {
    margin: auto 5px;
    width: 30px;
    height: 30px;
    border: 1px solid grey;
    border-radius: 15px;
}

.task-item button:hover {
    cursor: pointer;
    border: 1px solid rgb(44, 44, 44);
    box-shadow: 1px 1px 1px rgb(44, 44, 44);
}

.done {
    background: linear-gradient(to right, rgba(0, 173, 0, 0.6), rgba(0, 97, 0, 0.6));
}

.pending {
    color: white;
    background: linear-gradient(to right, rgba(108, 0, 196, 0.6), rgba(78, 0, 141, 0.6));
}

@media (max-width: 1024px) and (min-width: 768px) {
  .tasks {
    width: 75vw;
  }
}

@media (max-width: 768px){
  .tasks {
    width: 100vw;
  }
  .task-item {
    font-size: 0.8rem;
    width: 95vw;
  }
}

</style>
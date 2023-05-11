<template>
  <div class="register">
    <form class="add-task">
        <input type="text" name="task" id="task" placeholder="Nova tarefa" autofocus v-model="task">
        <button @click.prevent="createTask()">Criar</button>
    </form>
  </div>
</template>

<script>

export default {
    name: 'CompRegister',
    data() {
        return {
            task: '',
        }
    },
    methods: {
        createTask() {
            let newTask = this.task
            this.$emit('taskListEvent', newTask)
            this.task = ''
        }
    }
}
</script>

<style>
.register {
    grid-area: register;
    display: flex;
    justify-content: center;
    align-items: center;
    margin-bottom: 10px;
    width: 65vw;
    height: 10vh;
}

.add-task {
    display: inline-flex;
    width: 500px;
    height: 35px;
}

.add-task input {
    font-size: 1rem;
    outline: none;
    color: black;
    padding-left: 5px;
    width: 100%;
    background: linear-gradient(to right, rgb(201, 201, 201, 0.5), rgb(134, 134, 134, 0.5));
    border: 1px solid rgb(39, 39, 39);
    border-width: 1px 0 1px 1px;
    border-top-left-radius: 3px;
    border-bottom-left-radius: 3px;
}

::placeholder {
  color: black;
}

.add-task button {
    font-size: 1rem;
    outline: none;
    color: white;
    background-color: rgb(82, 45, 150, 0.5);
    border: 1px solid rgb(39, 39, 39);
    border-top-right-radius: 3px;
    border-bottom-right-radius: 3px;
}

.add-task button:hover {
    cursor: pointer;
    border: 1px solid black;
}

@media (max-width: 1024px) and (min-width: 768px) {
  .register {
    width: 75vw;
  }
}

@media (max-width: 768px){
  .register {
    width: 100vw;
  }
  .add-task {
    width: 95vw;
  }
}

</style>
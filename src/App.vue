<template>
  <div id="main">
    <h1>#todos</h1>
    <ButtonGroup :buttons="btns" @selected-filter="gg" />
    <TodoList :tasks="filterTasks(filterOption.filter, tasks)" @task-checked="taskChecked"/>
  </div>
</template>

<script setup>
import { reactive, watch } from 'vue';
import ButtonGroup from './components/ButtonGroup.vue';
import TodoList from './components/TaskList.vue';

const tasks = reactive([
  {
    taskId: 1,
    task: "Kupi Sarmu",
    isDone: false,
  },
  {
    taskId: 2,
    task: "Kupi sira braleeee",
    isDone: false,
  },
  {
    taskId: 3,
    task: "Kupi secer braleeeee",
    isDone: false,
  }
]);

// Values for buttons
const btns = reactive([
    {
        id: 0,
        title: "All",
        selected: false,
        filterEmit: "all"
    },
    {
        id: 1,
        title: "Active",
        selected: false,
        filterEmit: "active"
    },
    {
        id: 2,
        title: "Completed",
        selected: false,
        filterEmit: "completed"
    }
]);

// Holds selected filter state
const filterOption = reactive({
  filter: 'all',
});

// Function that filters tasks based on filter option
const filterTasks = (option, tasks) => {
  switch(option) {
    case 'all':
      return tasks;
    case 'active':
      return tasks.filter(task => !task.isDone);
    case 'completed':
      return tasks.filter(task => task.isDone);
  }
}

// Function that get's called when checkbox on task is checked.
// It get's task id as a parameter from TaskItem,
// and than filters array of tasks to find task that is checked and sets isDone to true
const taskChecked = (id) => {
  tasks.filter(task => task.taskId === id)[0].isDone = true;
}

const gg = (id) => {
  console.log('Radi', id);
  btns.forEach(option => option.id === id ? option.selected = true : option.selected = false);
}

watch(btns, (newState) => {
  filterOption.filter = newState.filter(option => option.selected )[0].filterEmit;
})
</script>

<style lang="scss">
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}

#main {
  width: 70%;
  margin: 0 auto;
}
</style>

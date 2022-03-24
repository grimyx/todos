<template>
  <div id="main">
    <h1>#todos</h1>
    <ButtonGroup :buttons="btns" @selected-filter="selectSortButton" />
    <TaskInput v-if="!btns[2].selected" @task-name="newTask"/>
    <TodoList :tasks="filterTasks(filterOption.filter, tasks)" @task-checked="taskChecked" @delete-task="deleteTask"/>
  </div>
</template>

<script setup>
import { reactive, watch } from 'vue';
import ButtonGroup from './components/ButtonGroup.vue';
import TodoList from './components/TaskList.vue';
import TaskInput from './components/TaskInput.vue';
//import { getTasks, setTasks } from './TasksModel';

const tasks = reactive([
  {
    taskId: 0,
    task: "Buy bread",
    isDone: false,
  },
  {
    taskId: 1,
    task: "Go to school",
    isDone: false,
  },
  {
    taskId: 2,
    task: "Watch Star Wars",
    isDone: false,
  }
]);


// Values for buttons
const btns = reactive([
    {
        id: 0,
        title: "All",
        selected: true,
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

const selectSortButton = (id) => {
  btns.forEach(option => option.id === id ? option.selected = true : option.selected = false);
}

// deleteTask - deletes task from list of tasks
// params:
// id - id of task we want to delete
const deleteTask = (id) => {
  const s = tasks.filter(task => task.taskId === id);
  const index = tasks.indexOf(s[0]);
  tasks.splice(index, 1);
}

// newTask - creates new task object with task value from input that user entered
// Value of taskId is size of tasks array, since task id starts from 0
// isDone is set to false by default
// params: 
// task - task name, String
const newTask = (task) => {
  tasks.push({
    taskId: tasks.length,
    task: task,
    isDone: false
  })
};

watch(btns, (newState) => {
  filterOption.filter = newState.filter(option => option.selected )[0].filterEmit;
});


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
  color: #2c3e50;
  margin-top: 60px;
}

#main {
  width: 70%;
  margin: 0 auto;
}

h1 {
  text-align: center;
}
</style>

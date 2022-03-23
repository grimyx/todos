<template>
<div id="list-container">
    <div v-for="task in props.tasks" :key="task.taskId">
        <TaskItem 
            v-bind="task"  
            @task-checked="$emit('task-checked', $event)"
            @delete-task="$emit('delete-task', $event)"
        />
    </div>
</div>
</template>

<script setup>
import TaskItem from './TaskItem.vue';

const props = defineProps(['tasks']);


</script>

<style scoped>
#list-container {
    margin-top: 1rem;
}
</style>
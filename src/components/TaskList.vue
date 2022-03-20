<template>
<div>
    <div v-for="task in props.tasks" :key="task.taskId">
        <TaskItem v-bind="task"  @task-checked="$emit('task-checked', $event)"/>
    </div>
</div>
</template>

<script setup>
import TaskItem from './TodoItem.vue';

const props = defineProps(['tasks']);


</script>
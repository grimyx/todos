<template>
    <div id="todo-item">
        <input type="checkbox" :disabled="props.isDone" 
        :checked="props.isDone" @change="$emit('task-checked', props.taskId)"/>
        <p>{{props.task}}</p>
        <IconButton :icon="deleteIcon" :onClick="() => console.log(props.taskId) " />
    </div>
</template>

<script setup>
import IconButton from './IconButton.vue';
const props = defineProps(['taskId', 'task', 'isDone']);

const deleteIcon = 'delete';
</script>

<style scoped>
#todo-item {
    display: flex;
}

input:disabled {
    color: blue;
}

delete-btn {
    justify-self: flex-end;
}
/* stil ide posle */
</style>
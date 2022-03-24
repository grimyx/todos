<template>
    <div id="todo-item">
        <input type="checkbox" :disabled="props.isDone" 
        :checked="props.isDone" @change="$emit('task-checked', props.taskId)"/>
        <p :class="{'strike-text' : props.isDone}">{{props.task}}</p>
        <IconButton :icon="deleteIcon" @click="$emit('delete-task', props.taskId)" v-if="props.isDone" />
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
    margin: 0.5rem 0;
    width: 100%;
    align-items: center;
}


input {
    width: 24px;
    height: 24px;
    margin-right: 1rem;
    justify-self: flex-start;
}

input:disabled {
    color: blue;
}

delete-btn {
    justify-self: flex-end;
}

.strike-text {
    text-decoration: line-through;
}
</style>
<template>
    <div id="todo-item">
        <input type="checkbox" :checked="props.isDone"/>
        <p>{{props.task}}</p>
    </div>
</template>

<script setup>

const props = defineProps(['task', 'isDone']);

</script>

<style scoped>
#todo-item {
    display: flex;
}

/* stil ide posle */
</style>
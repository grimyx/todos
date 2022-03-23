<template>

<div id="task-input">
    <MyInput class="inputField" v-model="task"/>
    <MyButton size="lg" color="primary" @click="$emit('task-name', task)">Add</MyButton>
</div>
</template>

<script setup>
import { ref } from 'vue';

import MyInput from './MyInput.vue';
import MyButton from './MyButton.vue';

// use .value to access refs and change them 
// note to myself
const task = ref("");

</script>

<style scoped>
size-md {
    width: 50%;
}

#task-input {
    display: flex;
    justify-content: space-between;
    align-items: center;
    margin-top: 1rem;
}

.inputField {
    width: 90%;
}
</style>


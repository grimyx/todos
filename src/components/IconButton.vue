<template>
<div id="icon-button">
    <span class="material-icons" @click="props.onClick">{{ props.icon }}</span>
</div>
</template>

<script setup>

const props = defineProps([
    'icon',
    'onClick'
]);
</script>

<style>
#icon-button:hover, :focus {
    color:red;
}
</style>
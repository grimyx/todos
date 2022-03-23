<template>
<div id="icon-button">
    <span class="material-icons">{{props.icon}}</span>
</div>
</template>

<script setup>

const props = defineProps(['icon']);
</script>

<style scoped>
#icon-button {
    cursor:default;
    display: flex;

    /* floats to right */
    margin-left: auto;
}

#icon-button:hover, :focus {
    color:red;
}
</style>
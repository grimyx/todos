<template>
    <div id="tabs">
        <span class="filter-option" 
            :class="{'option-selected': btn.selected}" 
            v-for="btn in props.buttons" :key="btn.id" 
            @click="$emit('selected-filter',btn.id)">{{ btn.title }}
        </span>
    </div>
</template>

<script setup>

const props = defineProps(['buttons']);

</script>

<style lang="scss" scoped>
#tabs {
    display: flex;
    justify-content: space-around;
    border-bottom: 1px solid #BDBDBD;
    cursor: default;
}

.option-selected { 
    border-bottom: 2px solid blue;
}

.filter-option:hover{
    border-bottom: 2px solid black;
}
</style>
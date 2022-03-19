<template>
    <div id="tabs">
        <span class="filter-option" 
            :class="{'option-selected': btn.selected}" 
            v-for="btn in btns" :key="btn.id" 
            @click="selectOption(btn.id)">{{ btn.title }}
        </span>
    </div>
</template>

<script setup>
import { reactive, watch } from 'vue';

const btns = reactive([
    {
        id: 0,
        title: "All",
        selected: false,
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

const emits = defineEmits(['selected-filter']);

watch(btns, (newBtns) => {
    const e = (newBtns.filter(btn => btn.selected))[0].filterEmit;
    emits('selected-filter', e);
})

const selectOption = (id) => {
   btns.forEach(option => option.id === id ? option.selected = true : option.selected = false);
}
</script>

<style lang="scss" scoped>
#tabs {
    display: flex;
    justify-content: space-around;
    border-bottom: 1px solid #BDBDBD;
}

.option-selected { 
    border-bottom: 2px solid blue;
}

.filter-option:hover{
    border-bottom: 2px solid black;
}
</style>
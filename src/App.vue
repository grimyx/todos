<template>
<h1>#todos</h1>
<ButtonGroup @selected-filter="gg"/>
<hr />
</template>

<script setup>
import ButtonGroup from './components/ButtonGroup.vue';

const gg = (g) => {
  console.log(g);
}
</script>

<style lang="scss">
* {
  margin:0;
  padding: 0;
  box-sizing: border-box;
}

#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

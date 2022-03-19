<template>
<h1>#todos</h1>
<Tabs />
</template>

<script setup>
import Tabs from './components/Tabs.vue';

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

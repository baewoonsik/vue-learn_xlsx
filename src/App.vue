<template>
  <div id="app">
    <LearnXlsx />
  </div>
</template>

<script>
import LearnXlsx from './components/LearnXlsx.vue';

export default {
  name: 'App',
  components: {
    LearnXlsx
  },
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>

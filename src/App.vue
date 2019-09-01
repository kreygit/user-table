<template>
  <div id="app">
    <!-- <TestReload /> -->
    <UserTable />
  </div>
</template>

<script>
import UserTable from './components/UserTable'
import TestReload from './components/TestReload'

export default {
  name: 'app',
  components: {
    UserTable,
    TestReload
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  /* text-align: center; */
  color: #2c3e50;
  margin-top: 2%;
}
</style>


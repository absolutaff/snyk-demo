<template>
  <div id="app">
    <DependencyLoader />
  </div>
</template>

<script>
import DependencyLoader from './components/DependencyLoader'

export default {
  name: 'App',
  components: {
    DependencyLoader
  }
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

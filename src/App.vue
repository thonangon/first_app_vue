<template>
  <AppView/>
</template>

<script>
import AppView from './components/AppView.vue'
export default {
  name: 'App',
  components:{
    AppView
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

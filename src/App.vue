<template>
  <div id="app">
     <Header/>
    <router-view/>
  </div>
</template>
<script>
import Header from './components/layout/Header.vue'
export default {
  name : 'App',
  components :  {
    Header
  }
}
</script>
<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
 
}

#nav {
  padding: 30px;
}
</style>

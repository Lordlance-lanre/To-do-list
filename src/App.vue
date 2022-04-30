<template>
  <h1>{{ title }}</h1>
  <Inputbox />
</template>

<script>
import Inputbox from './components/Inputbox.vue'

export default {
  name: 'App',
  components: { Inputbox },
  data() {
    return {
      title: 'To do list App'
    }
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

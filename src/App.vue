<template>
  <div id="app">
    <home/>
  </div>
</template>
<script>
import Home from './views/Home'

export default {
  components: {
    Home
  },
  mounted() {
    // img not found at Github Pages
    const { NODE_ENV } = process.env;
    document.documentElement.className = NODE_ENV;
  }
}

</script>
<style>

</style>

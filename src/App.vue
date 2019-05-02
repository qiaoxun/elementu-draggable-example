<template>
  <div id="app">
    <el-tabs type="card">
      <el-tab-pane label="Simple Demo">
        <simple-demo/>
      </el-tab-pane>
      <el-tab-pane label="Test">Test</el-tab-pane>
    </el-tabs>
  </div>
</template>
<script>
import SimpleDemo from './components/SimpleDemo'

export default {
  components: {
    SimpleDemo
  }
}

</script>
<style>

</style>

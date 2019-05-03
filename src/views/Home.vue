<template>
  <div id="app">
    <el-tabs type="card">
      <el-tab-pane label="Simple">
        <simple/>
      </el-tab-pane>
      <el-tab-pane label="Two Lists">
        <two-lists/>
      </el-tab-pane>
      <el-tab-pane label="Clone">
        <clone/>
      </el-tab-pane>
      <el-tab-pane label="Custom Clone">
        <custom-clone/>
      </el-tab-pane>
      <el-tab-pane label="Clone on Control">
        <clone-on-control/>
      </el-tab-pane>
      <el-tab-pane label="Handle">
        <handle/>
      </el-tab-pane>
      <el-tab-pane label="ComponentData">
        <component-data/>
      </el-tab-pane>
      <el-tab-pane label="Transition">
        <transition/>
      </el-tab-pane>
      <el-tab-pane label="Transitions">
        <transitions/>
      </el-tab-pane>
      <el-tab-pane label="Table Item">
        <table-item/>
      </el-tab-pane>
      <el-tab-pane label="Table Column">
        <table-column/>
      </el-tab-pane>
      <el-tab-pane label="Footer Solt">
        <footer-solt/>
      </el-tab-pane>
      <el-tab-pane label="Header Solt">
        <header-solt/>
      </el-tab-pane>
    </el-tabs>
  </div>
</template>
<script>
import simple from '@/components/simple-demo'
import TwoLists from '@/components/two-lists-demo'
import clone from '@/components/clone-demo'
import CustomClone from '@/components/custom-clone-demo'
import CloneOnControl from '@/components/clone-on-control-demo'
import handle from '@/components/handle-demo'
import ComponentData from '@/components/component-data-demo'
import Transition from '@/components/transition-demo'
import Transitions from '@/components/transitions-demo'
import TableItem from '@/components/table-item-demo'
import TableColumn from '@/components/table-column-demo'
import FooterSolt from '@/components/footer-solt-demo'
import HeaderSolt from '@/components/header-solt-demo'

export default {
  components: {
    simple,
    TwoLists,
    clone,
    CustomClone,
    CloneOnControl,
    handle,
    ComponentData,
    Transition,
    Transitions,
    TableItem,
    TableColumn,
    FooterSolt,
    HeaderSolt
  }
}

</script>
<style>

</style>

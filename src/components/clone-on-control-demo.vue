<template>
  <div>
    <el-row>
      <el-col :span="24" style="padding: 10px 10px;">
        <span style="color: red;">Press Ctrl to clone element from list 1</span>
      </el-col>
    </el-row>
    <el-row>
      <el-col :span="6" style="padding: 10px 10px;">
        <h3>Draggable 1</h3>
        <draggable
          :list="list1"
          ghost-class="ghost"
          :group="{ name: 'people', pull: pullFunction }"
          :clone="onClone"
          @start="onStart"
          >

          <div
            class="item"
            v-for="element in list1"
            :key="element.name">
            {{ element.name }}
          </div>
        </draggable>
      </el-col>

      <el-col :span="6" style="padding: 10px 10px;">
        <h3>Draggable 2</h3>
        <draggable
          :list="list2"
          ghost-class="ghost"
          group="people">

          <div
            class="item"
            v-for="element in list2"
            :key="element.id">
            {{ element.name }}
          </div>
        </draggable>
      </el-col>

      <el-col :span="6" style="padding: 10px 10px;">
        <raw-display class="col-3" :value="list1" title="List1"></raw-display>
      </el-col>

      <el-col :span="6" style="padding: 10px 10px;">
        <raw-display class="col-3" :value="list2" title="List2"></raw-display>
      </el-col>
    </el-row>


    <el-row>
      <el-col :span="24" style="padding: 10px 10px;" >
        <h3>Properties</h3>
        <list/>
        <group/>
        <ghost-class/>
        <start/>
        <clone-property/>
      </el-col>
    </el-row>
  </div>
</template>

<script>
import draggable from "vuedraggable";
import RawDisplay from './raw-display';
import list from './properties/list';
import GhostClass from './properties/ghost-class';
import group from './properties/group';
import start from './properties/start';
import CloneProperty from './properties/clone-property';

let idGlobal = 8;

export default {
  name: "clone-on-control",
  display: "Clone on Control",
  instruction: "Press Ctrl to clone element from list 1",
  order: 1,
  components: {
    draggable,
    RawDisplay,
    list,
    GhostClass,
    group,
    start,
    CloneProperty
  },
  data() {
    return {
      list1: [
        { name: "John", id: 0 },
        { name: "Joao", id: 1 },
        { name: "Jean", id: 2 },
        { name: "Gerard", id: 4 }
      ],
      list2: [
        { name: "Juan", id: 5 },
        { name: "Edgard", id: 6 },
        { name: "Johnson", id: 7 }
      ],
      controlOnStart: true
    };
  },
  methods: {
    onClone({name}) {
      return {
        id: idGlobal++,
        name: name
      };
    },
    pullFunction() {
      return this.controlOnStart ? "clone" : true;
    },
    onStart({ originalEvent }) {
      this.controlOnStart = originalEvent.ctrlKey;
    }
  }
};
</script>
<style scoped>
.buttons {
  margin-top: 35px;
}

.ghost {
  opacity: 0.5;
  background-color: red;
}

.item {
  padding: 10px 10px;
  border: 1px solid #dcdfe6;
}
</style>

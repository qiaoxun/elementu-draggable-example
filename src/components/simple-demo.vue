<template>
  <div>
    <el-row>
      <el-col :span="4">
        <el-button type="primary" @click="add">Add</el-button>
        <el-button type="success" @click="replace">Replace</el-button>
        <el-checkbox id="disabled" v-model="enabled">DnD enabled</el-checkbox>
      </el-col>

      <el-col :span="4" style="padding: 10px 10px;">
        <h3>Draggable List {{ draggingInfo }}</h3>

        <draggable
          :list="list"
          :disabled="!enabled"
          ghost-class="ghost"
          @start="dragging = true"
          @end="dragging = false">

          <div
            class="item"
            v-for="element in list"
            :key="element.id"
          >
            {{ element.name }}
          </div>
        </draggable>
      </el-col>

      <el-col :span="8" style="padding: 10px 10px;">
        <h3>Draggable button {{ draggingInfo }}</h3>
        <draggable
          :list="list"
          :disabled="!enabled"
          class="list-group"
          ghost-class="ghost"
          @start="onStart"
          @end="onEnd">

          <el-button v-for="element in list" :key="element.name" size="small">{{ element.name }}</el-button>

        </draggable>
      </el-col>

      <el-col :span="6" style="padding: 10px 10px;">
        <raw-display class="col-3" :value="list" title="List"></raw-display>
      </el-col>
    </el-row>

    <el-row>
      <el-col :span="24" style="padding: 10px 10px;" >
        <h3>Properties</h3>
        <list/>
        <disabled/>
        <ghost-class/>
        <start/>
        <end/>
      </el-col>
    </el-row>
  </div>
</template>

<script>
import draggable from "vuedraggable";
import RawDisplay from './raw-display';
import list from './properties/list';
import start from './properties/start';
import end from './properties/end';
import disabled from './properties/disabled';
import GhostClass from './properties/ghost-class';


let id = 1;
export default {
  name: "simple",
  display: "Simple",
  order: 0,
  components: {
    draggable,
    RawDisplay,
    list,
    disabled,
    GhostClass,
    start,
    end
  },
  data() {
    return {
      enabled: true,
      list: [
        { name: "John", id: 0 },
        { name: "Joao", id: 1 },
        { name: "Jean", id: 2 }
      ],
      dragging: false
    };
  },
  computed: {
    draggingInfo() {
      return this.dragging ? "under drag" : "";
    }
  },
  methods: {
    add() {
      this.list.push({ name: "Juan " + id, id: id++ });
    },
    replace() {
      this.list = [{ name: "Edgard", id: id++ }];
    },
    onStart(evt) {
      this.dragging = true;
      console.log('start evt', evt)
    },
    onEnd(evt) {
      this.dragging = false;
      console.log('end evt', evt)
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
  background: red;
}

.item {
  padding: 10px 10px;
  border: 1px solid #dcdfe6;
}
</style>

<template>
  <div>
    <el-row>
      <el-col :span="14" style="padding: 10px 10px;">
        <h3>Draggable with header</h3>

        <draggable
          :list="list"
          class="list-group"
          draggable=".item"
          @start="dragging = true"
          @end="dragging = false"
        >
          <div
            class="item"
            v-for="element in list"
            :key="element.id">
            {{ element.name }}
          </div>

          <div
            slot="header"
            class="btn-group list-group-item"
            role="group"
            aria-label="Basic example">
            <el-button type="primary" @click="add">Add</el-button>
            <el-button type="success" @click="replace">Replace</el-button>
          </div>
        </draggable>
      </el-col>

      <el-col :span="10" style="padding: 10px 10px;">
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
        <move/>
        <draggable-prop/>
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
import move from './properties/move';
import DraggableProp from './properties/draggable';

let id = 1;
export default {
  name: "headerslot",
  display: "Header slot",
  order: 14,
  components: {
    draggable,
    RawDisplay,
    list,
    disabled,
    GhostClass,
    start,
    end,
    move,
    DraggableProp
  },
  data() {
    return {
      list: [
        { name: "John 1", id: 0 },
        { name: "Joao 2", id: 1 },
        { name: "Jean 3", id: 2 }
      ],
      dragging: false
    };
  },
  methods: {
    add: function() {
      this.list.push({ name: "Juan " + id, id: id++ });
    },
    replace: function() {
      this.list = [{ name: "Edgard", id: id++ }];
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

.flip-list-move {
  transition: transform 0.5s;
}
.no-move {
  transition: transform 0s;
}

.list-group-item {
    position: relative;
    display: block;
    padding: .75rem 1.25rem;
    margin-bottom: -1px;
    background-color: #fff;
    border: 1px solid rgba(0,0,0,.125);
}
</style>

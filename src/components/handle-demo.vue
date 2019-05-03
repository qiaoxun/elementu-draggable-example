<template>
  <div>
    <el-row>
      <el-col :span="4">
        <el-button type="primary" @click="add">Add</el-button>
      </el-col>

      <el-col :span="10" style="padding: 10px 10px;">
        <h3>Draggable List {{ draggingInfo }}</h3>

        <draggable
          tag="ul"
          handle=".handle"
          :list="list"
          @start="dragging = true"
          @end="dragging = false">
          <li class="list-group-item"
           v-for="(element, idx) in list"
           :key="element.id">
           <i class="el-icon-s-unfold handle"></i>
           <span class="text">{{ element.name }}</span>
           <el-input placeholder="Please input" v-model="element.text" style="width: 200px;"></el-input>
           <i class="el-icon-close close" @click="removeAt(idx)"></i>
          </li>
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
        <tag/>
        <handle-property/>
      </el-col>
    </el-row>
  </div>
</template>

<script>
import draggable from "vuedraggable";
import RawDisplay from './raw-display';
import list from './properties/list';
import tag from './properties/tag';
import HandleProperty from './properties/handle';


let id = 2;
export default {
  name: "handle",
  display: "Handle",
  order: 0,
  components: {
    draggable,
    RawDisplay,
    list,
    tag,
    HandleProperty
  },
  data() {
    return {
      list: [
        { name: "John", text: "", id: 0 },
        { name: "Joao", text: "", id: 1 },
        { name: "Jean", text: "", id: 2 }
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
    removeAt(idx) {
      this.list.splice(idx, 1);
    },
    add() {
      id++;
      this.list.push({name: "Joey" + id, id, text: ""})
    }
  }
};
</script>
<style scoped>
.button {
  margin-top: 35px;
}
.handle {
  float: left;
  padding-top: 8px;
  padding-bottom: 8px;
}
.close {
  float: right;
  padding-top: 8px;
  padding-bottom: 8px;
}
input {
  display: inline-block;
  width: 50%;
}
.text {
  margin: 20px;
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

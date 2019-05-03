<template>
  <div>
    <el-row>
      <el-col :span="14" style="padding: 10px 10px;">
        <h3>Draggable List {{ draggingInfo }}</h3>
        <draggable tag="el-collapse" :list="list" :component-data="getComponentData()">
          <el-collapse-item v-for="e in list" :title="e.title" :name="e.name" :key="e.name">
            {{ e.description }}
          </el-collapse-item>
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
        <component-data-property/>
      </el-col>
    </el-row>
  </div>
</template>

<script>
import draggable from "vuedraggable";
import RawDisplay from './raw-display';
import list from './properties/list';
import tag from './properties/tag';
import ComponentDataProperty from './properties/component-data';

export default {
  name: "ComponentData",
  display: "ComponentData Demo",
  order: 0,
  components: {
    draggable,
    RawDisplay,
    list,
    tag,
    ComponentDataProperty
  },
  data() {
    return {
      enabled: true,
      activeNames: [],
      list: [
        { title: "title1", name: "John", id: 0, description: "this is title 1" },
        { title: "title2", name: "Joao", id: 1, description: "this is title 2" },
        { title: "title3", name: "Jean", id: 2, description: "this is title 3" }
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
    handleChange() {
      console.log('this.activeNames', this.activeNames)
      console.log('changed')
    },
    inputChanged(value) {
      this.activeNames = value;
    },
    getComponentData() {
      return {
        on: {
          change: this.handleChange,
          input: this.inputChanged
        },
        props: {
          value: this.activeNames
        }
      };
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

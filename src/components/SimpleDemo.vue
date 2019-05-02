<template>
  <el-row>
    <el-col :span="4">
      <el-button type="primary" @click="add">Add</el-button>
      <el-button type="success" @click="replace">Replace</el-button>
      <el-checkbox id="disabled" v-model="enabled">DnD enabled</el-checkbox>
    </el-col>

    <el-col :span="9" style="margin: 10px 10px;">
      <h3>Draggable List {{ draggingInfo }}</h3>

      <draggable
        :list="list"
        :disabled="!enabled"
        class="list-group"
        ghost-class="ghost"
        @start="dragging = true"
        @end="dragging = false">

        <div
          class="item"
          v-for="element in list"
          :key="element.name"
        >
          {{ element.name }}
        </div>
      </draggable>
    </el-col>

    <el-col :span="9" style="margin: 10px 10px;">
      <h3>Draggable button {{ draggingInfo }}</h3>
      <draggable
        :list="list"
        :disabled="!enabled"
        class="list-group"
        ghost-class="ghost"
        @start="dragging = true"
        @end="dragging = false">

        <el-button v-for="element in list" :key="element.name" size="small">{{ element.name }}</el-button>

      </draggable>
    </el-col>

  </el-row>
</template>

<script>
import draggable from "vuedraggable";
let id = 1;
export default {
  name: "simple",
  display: "Simple",
  order: 0,
  components: {
    draggable
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
  background: #c8ebfb;
}

.item {
  padding: 10px 10px;
  border: 1px solid #dcdfe6;
}
</style>

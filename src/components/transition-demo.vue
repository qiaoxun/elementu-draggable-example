<template>
  <div>
    <el-row>
      <el-col :span="4">
        <el-button type="primary" @click="sort">To original order</el-button>
      </el-col>

      <el-col :span="7" style="padding: 10px 10px;">
        <h3 style="padding-left: 50px;">Transition Group</h3>
        <draggable :list="list" tag="ul" v-bind="dragOptions">
          <transition-group type="transition" name="flip-list">
            <li class="list-group-item" v-for="element in list" :key="element.order">
              <i>
                {{ element.name }}
              </i>
            </li>
          </transition-group>
        </draggable>
      </el-col>

      <el-col :span="7" style="padding: 10px 10px;">
        <h3 style="padding-left: 50px;">Without Transition Group</h3>
        <draggable :list="list" tag="ul" v-bind="dragOptions2">
          <li class="list-group-item" v-for="element in list" :key="element.order">
            <i>
              {{ element.name }}
            </i>
          </li>
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
        <animation/>
        <tag/>
      </el-col>
    </el-row>
  </div>
</template>

<script>
import draggable from "vuedraggable";
import RawDisplay from './raw-display';
import list from './properties/list';
import animation from './properties/animation';
import tag from './properties/tag';

const message = [
  "vue.draggable",
  "draggable",
  "component",
  "for",
  "vue.js 2.0",
  "based",
  "on",
  "Sortablejs"
];

export default {
  name: "transition",
  display: "Transition",
  order: 7,
  components: {
    draggable,
    RawDisplay,
    list,
    animation,
    tag
  },
  data() {
    return {
      list: message.map((name, index) => {
        return {name, order: index + 1}
      })
    };
  },
  methods: {
    sort() {
      this.list = this.list.sort((a, b) => a.order - b.order);
    }
  },
  computed: {
    dragOptions() {
      return {
        animation: 0,
        group: "description",
        disabled: false
      }
    },
    dragOptions2() {
      return {
        animation: 0,
        group: "description2",
        disabled: false
      }
    }
  }
};
</script>
<style scoped>
.button {
  margin-top: 35px;
}
.flip-list-move {
  transition: transform 0.5s;
}
.no-move {
  transition: transform 0s;
}
.ghost {
  opacity: 0.5;
  background: red;
}
.list-group {
  min-height: 20px;
}
.list-group-item {
    position: relative;
    display: block;
    padding: .75rem 1.25rem;
    margin-bottom: -1px;
    background-color: #fff;
    border: 1px solid rgba(0,0,0,.125);
}
.list-group-item i {
  cursor: pointer;
}
</style>

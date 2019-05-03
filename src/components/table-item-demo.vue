<template>
  <div>
    <el-row>
      <el-col :span="14" style="padding: 10px 10px;">
        <table class="el-table">
          <thead class="has-gutter">
            <tr>
              <th class="el-table_137_column_557 is-leaf" v-for="column in tableHead" :key="column">
                <div class="cell">{{ column }}</div>
              </th>
            </tr>
          </thead>

          <draggable tag="tbody" :list="tableData" ghost-class="ghost">
            <tr class="el-table__row" v-for="(data, idx) in tableData" :key="idx">
              <td rowspan="1" colspan="1" class="el-table_127_column_509" v-for="columnData in data" :key="columnData">
                <div class="cell">{{ columnData }}</div>
              </td>
            </tr>
          </draggable>

        </table>

      </el-col>

      <el-col :span="10" style="padding: 10px 10px;">
        <raw-display class="col-3" :value="tableData" title="Table Data"></raw-display>
      </el-col>
    </el-row>

    <el-row>
      <el-col :span="24" style="padding: 10px 10px;" >
        <h3>Properties</h3>
        <list/>
        <ghost-class/>
        <tag/>
      </el-col>
    </el-row>
  </div>
</template>

<script>
import draggable from "vuedraggable";
import RawDisplay from './raw-display';
import list from './properties/list';
import GhostClass from './properties/ghost-class';
import tag from './properties/tag';

export default {
  name: "table-item-demo",
  display: "Table Item",
  order: 9,
  components: {
    draggable,
    RawDisplay,
    list,
    GhostClass,
    tag
  },
  data() {
    return {
      tableHead:['date', 'name', 'address'],
      tableData: [{
        date: '2016-05-03',
        name: 'Tom',
        address: 'No. 189, Grove St, Los Angeles'
      }, {
        date: '2016-05-02',
        name: 'Tom',
        address: 'No. 189, Grove St, Los Angeles'
      }, {
        date: '2016-05-04',
        name: 'Tom',
        address: 'No. 189, Grove St, Los Angeles'
      }, {
        date: '2016-05-01',
        name: 'Tom',
        address: 'No. 189, Grove St, Los Angeles'
      }]
    };
  }
};
</script>
<style scoped>
.el-table {
    position: relative;
    overflow: hidden;
    box-sizing: border-box;
    flex: 1;
    width: 100%;
    max-width: 100%;
    background-color: #fff;
    font-size: 14px;
    color: #606266;
}

.el-table thead {
    color: #909399;
    font-weight: 500;
}

.el-table__body, .el-table__footer, .el-table__header {
    table-layout: fixed;
    border-collapse: separate;
}

.el-table th {
    white-space: nowrap;
    overflow: hidden;
    user-select: none;
    background-color: #fff;
}

.el-table td, .el-table th {
    padding: 12px 0;
    min-width: 0;
    box-sizing: border-box;
    text-overflow: ellipsis;
    vertical-align: middle;
    position: relative;
    text-align: left;
}

.el-table td, .el-table th.is-leaf {
    border-bottom: 1px solid #ebeef5;
}

.ghost {
  opacity: 0.5;
  background: red;
}
</style>

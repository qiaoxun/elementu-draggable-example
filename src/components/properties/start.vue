<template>
  <el-row  style="border: 1px solid #dcdfe6;">
    <el-col :span="4" style="padding: 10px 10px;" >
      @start
    </el-col>
    <el-col :span="20" style="padding: 10px 10px;" >
      Start event, element dragging started. e.g @Start="onStart",
      and meantime inside methods properties,
      <br/>
      <code>
        onStart: function (/**Event*/evt) {<br/>
        &nbsp;&nbsp;evt.oldIndex;  // element index within parent<br/>
        },
      </code>
    </el-col>
  </el-row>
</template>

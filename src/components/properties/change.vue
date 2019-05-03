<template>
  <el-row  style="border: 1px solid #dcdfe6;">
    <el-col :span="4" style="padding: 10px 10px;" >
      change
    </el-col>
    <el-col :span="20" style="padding: 10px 10px;" >
      Called when dragging element changes position<br/>
      <code>
        onChange(evt) {<br/>
          &nbsp;&nbsp;// most likely why this event is used is to get the dragging element's current index<br/>
          &nbsp;&nbsp;console.log('evt', evt.newIndex)<br/>
          &nbsp;&nbsp;// same properties as onEnd<br/>
        }
      </code>
    </el-col>
  </el-row>
</template>

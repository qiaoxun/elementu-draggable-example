<template>
  <el-row  style="border: 1px solid #dcdfe6;">
    <el-col :span="4" style="padding: 10px 10px;" >
      clone
    </el-col>
    <el-col :span="20" style="padding: 10px 10px;" >
      Called when creating a clone of element<br/>
      <code>
        // Called when creating a clone of element<br/>
      	onClone: function (/**Event*/evt) {<br/>
      		&nbsp;&nbsp;var origEl = evt.item;<br/>
      		&nbsp;&nbsp;var cloneEl = evt.clone;<br/>
      	}<br/>
      </code>
      If we want to change cloned item, just return updated item on onClone function.<br/>
      <code>
        onClone({id, name}) {<br/>
          &nbsp;&nbsp;return {<br/>
            &nbsp;&nbsp;&nbsp;&nbsp;id: id++,<br/>
            &nbsp;&nbsp;&nbsp;&nbsp;name: `${name} ${id}`<br/>
          &nbsp;&nbsp;};<br/>
        }
      </code>
    </el-col>
  </el-row>
</template>

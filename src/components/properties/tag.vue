<template>
  <el-row  style="border: 1px solid #dcdfe6;">
    <el-col :span="4" style="padding: 10px 10px;" >
      tag
    </el-col>
    <el-col :span="20" style="padding: 10px 10px;" >
      <p>Type: <code>String</code><br>Default: <code>'div'</code></p>
      <p>HTML node type of the element that draggable component create as outer element for the included slot.<br>
It is also possible to pass the name of vue component as element. In this case, draggable attribute will be passed to the create component.<br>
See also componentData if you need to set props or event to the created component.</p>
    </el-col>
  </el-row>
</template>

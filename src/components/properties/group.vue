<template>
  <el-row  style="border: 1px solid #dcdfe6;">
    <el-col :span="4" style="padding: 10px 10px;" >
      group
    </el-col>
    <el-col :span="20" style="padding: 10px 10px;" >
      <p>To drag elements from one list into another, both lists must have the same <code>group</code> value.
      You can also define whether lists can give away, give and keep a copy (<code>clone</code>), and receive elements.</p>
      <ul>
        <li>name: <code>String</code> — group name</li>
        <li>pull: <code>true|false|["foo", "bar"]|'clone'|function</code> — ability to move from the list. <code>clone</code> — copy the item, rather than move. Or an array of group names which the elements may be put in. Defaults to <code>true</code>.</li>
        <li>put: <code>true|false|["baz", "qux"]|function</code> — whether elements can be added from other lists, or an array of group names from which elements can be added.</li>
        <li>revertClone: <code>boolean</code> — revert cloned element to initial position after moving to a another list.</li>
      </ul>
    </el-col>
  </el-row>
</template>

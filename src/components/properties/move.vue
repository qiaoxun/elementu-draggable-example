<template>
  <el-row  style="border: 1px solid #dcdfe6;">
    <el-col :span="4" style="padding: 10px 10px;" >
      move
    </el-col>
    <el-col :span="20" style="padding: 10px 10px;" >
      <p>Type: <code>Function</code><br>
      Required: <code>false</code><br>
      Default: <code>null</code><br></p>

      <p>If not null this function will be called in a similar way as Sortable onMove callback. Returning false will cancel the drag operation.</p>

      <div class="highlight highlight-source-js">
        <pre><span class="pl-k">function</span> <span class="pl-en">onMoveCallback</span>(<span class="pl-smi">evt</span>, <span class="pl-smi">originalEvent</span>){
          <span class="pl-k">...</span>
          <span class="pl-c"><span class="pl-c">//</span> return false; — for cancel</span>
        }</pre>
      </div>

      <p>evt object has same property as Sortable onMove event, and 3 additional properties:</p>

      <ul>
        <li><code>draggedContext</code>:  context linked to dragged element
        <ul>
        <li><code>index</code>: dragged element index</li>
        <li><code>element</code>: dragged element underlying view model element</li>
        <li><code>futureIndex</code>:  potential index of the dragged element if the drop operation is accepted</li>
        </ul>
        </li>
        <li><code>relatedContext</code>: context linked to current drag operation
        <ul>
        <li><code>index</code>: target element index</li>
        <li><code>element</code>: target element view model element</li>
        <li><code>list</code>: target list</li>
        <li><code>component</code>: target VueComponent</li>
        </ul>
        </li>
      </ul>

    </el-col>
  </el-row>
</template>

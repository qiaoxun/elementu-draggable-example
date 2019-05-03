<template>
  <el-row  style="border: 1px solid #dcdfe6;">
    <el-col :span="4" style="padding: 10px 10px;" >
      component-data
    </el-col>
    <el-col :span="20" style="padding: 10px 10px;" >
      <p>Type: <code>Object</code><br>
      Required: <code>false</code><br>
      Default: <code>null</code><br></p>
      <p>This props is used to pass additional information to child component declared by <a href="#tag">tag props</a>.<br>
        Value:</p>
      <ul>
        <li><code>props</code>: props to be passed to the child component</li>
        <li><code>attrs</code>: attrs to be passed to the child component</li>
        <li><code>on</code>: events to be subscribe in the child component</li>
      </ul>

      <p>Example (using <a href="http://element.eleme.io/#/en-US" rel="nofollow">element UI library</a>):</p>

      <img alt="component data" src="@/assets/component_data_property.png">

      <div class="highlight highlight-source-js">
        <pre>methods<span class="pl-k">:</span> {
          <span class="pl-en">handleChange</span>() {
            <span class="pl-en">console</span>.<span class="pl-c1">log</span>(<span class="pl-s"><span class="pl-pds">'</span>changed<span class="pl-pds">'</span></span>);
            },
            <span class="pl-en">inputChanged</span>(<span class="pl-smi">value</span>) {
              <span class="pl-c1">this</span>.<span class="pl-smi">activeNames</span> <span class="pl-k">=</span> value;
            },
            <span class="pl-en">getComponentData</span>() {
              <span class="pl-k">return</span> {
                on<span class="pl-k">:</span> {
                  change<span class="pl-k">:</span> <span class="pl-c1">this</span>.<span class="pl-smi">handleChange</span>,
                  input<span class="pl-k">:</span> <span class="pl-c1">this</span>.<span class="pl-smi">inputChanged</span>
                },
                attrs<span class="pl-k">:</span>{
                  wrap<span class="pl-k">:</span> <span class="pl-c1">true</span>
                },
                props<span class="pl-k">:</span> {
                  value<span class="pl-k">:</span> <span class="pl-c1">this</span>.<span class="pl-smi">activeNames</span>
                }
              };
            }
          }
        </pre>
      </div>
    </el-col>
  </el-row>
</template>

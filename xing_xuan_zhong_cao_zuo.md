### 表格行选中操作
***
本节主要介绍表格的行选中操作。
> 表格的行(tr)添加data-id属性可以激活行选中效果：`<tr data-id="001">`，table添加属性`data-selected-multi="true"`后，可以选中多行。
> 
  url参数上添加占位符`{#bjui-selected}`后，可获取选中行的id，多个id以`,`分隔。
>
  *示例代码如下：*
  ```html
<button type="button" class="btn-blue" data-url="remove.html?id={#bjui-selected}" data-toggle="doajax" data-confirm-msg="确定要删除选中项吗？" data-icon="remove">删除选中行</button>
<table class="table table-bordered" data-selected-multi="true">
  <thead>
      <tr>
          <th>No.</th>
          <th>姓名</th>
          <th>年龄</th>
      </tr>
  </thead>
  <tbody>
      <tr data-id="1">
          <td>1</td>
          <td>孙悟空</td>
          <td>5000</td>
      </tr>
      <tr data-id="2">
          <td>2</td>
          <td>唐僧</td>
          <td>4000</td>
      </tr>
      <tr data-id="3">
          <td>3</td>
          <td>猪八戒</td>
          <td>5500</td>
      </tr>
      <tr data-id="4">
          <td>4</td>
          <td>沙和尚</td>
          <td>5400</td>
      </tr>
  </tbody>
</table>
  ```


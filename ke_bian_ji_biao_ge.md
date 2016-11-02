### 可编辑表格
***
本节主要介绍框架的可编辑表格功能。
> 可编辑表格不支持多行表头。

#### 初始化
* Data属性：table添加属性`data-toggle="tabledit"`，并在表头定义好需要的编辑控件即可。

  *DOM示例代码：*
```html
<table class="table table-bordered table-hover table-striped table-top" data-toggle="tabledit">
    <thead>
        <tr>
            <th title="文本框"><input type="text" name="test[#index#].a1" placeholder="文本框"></th>
            <th title="复选框">
                <input type="checkbox" name="test[#index#].a2" id="doc-test-a2-1[#index#]" data-toggle="icheck" value="k1" data-label="选项一">
                <input type="checkbox" name="test[#index#].a2" id="doc-test-a2-2[#index#]" data-toggle="icheck" value="k2" data-label="选项二">
            </th>
            <th title="下拉菜单">
                <select name="test[#index#].a3" data-toggle="selectpicker">
                    <option value="a">甲</option>
                    <option value="b">乙</option>
                    <option value="c">丙</option>
                </select>
            </th>
            <th title="功能按钮"><button type="button" class="btn btn-default" data-toggle="dialog" data-url="doc/table/test.html" data-id="dialog-test" data-title="我的测试页面">打开测试</button></th>
            <th title="" data-addtool="true" width="100">
                <a href="ajaxDone2.html" class="btn btn-red row-del" data-confirm-msg="确定要删除该行信息吗？">删</a>
            </th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td> AAA |
            <td data-val="k2"> </td>
            <td data-val="c"> </td>
            <td data-original="true">-- </td>
            <td> -- </td>
        </tr>
    </tbody>
</table>
```
* jQuery API：
       $(table).tabledit(options)
       
### 参数（options）

| 名称 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| initnum | int | 0 | [可选] 默认初始化行数。 |
| action | string | null | [可选] 点完成或保存按钮后处理数据的服务端url。 |
| type | string | POST | [可选] 提交数据的方式。 |
| singleNoindex | boolean | false | [可选] 提交单行数据时，下标的index为0。 |
| callback | function(json) | [点我查看](#jump) | [可选] 回调函数。 |
| idname | string | id | `适用于 thead -> tr`[可选] 定义行数据的主键名称（id的name）。 |
| id | string | null | `适用于 tbody -> tr`[可选] 定义行数据的主键值（id的值）。 |
| addtool | boolean | false | `适用于 thead -> th`[可选] 表头列显示添加行控件。 |
| val | int | null | `适用于 tbody -> td`[可选] 对应表头定义input的值（如：radio/checkbox/select/上传控件）。 |
| notread | boolean | false | `适用于 tbody -> td`[可选] 设定本单元格的元素没有只读状态（如：功能按钮）。 |
***
#### 关于添加可编辑行
##### 初始化
* DOM属性：a链接或按钮添加属性`data-toggle="tableditadd"`，再设定目标表格`(data-target)`后，点击可为编辑表格添加行。

  *示例代码：*
```html
<button type="button" class="btn-green" data-toggle="tableditadd" data-target="#tabledit-id" data-num="1" data-icon="plus">添加编辑行</button>
```
* jQuery API：
```js
$(selector).tabledit('add', target, num)
```

##### 参数

| 名称 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| target | selector | null | [必选] 需要添加行的目标表格选择器。 |
| num | int | 1 | [可选] 每次添加的行数。 |


<span id="jump">
 ```js

function(json) {
    if (json[BJUI.keys.statusCode] == BJUI.statusCode.ok) {
        _doRead($tr)
    } else {
        $tr.bjuiajax('ajaxDone', json)
    }
}

```
 </span>





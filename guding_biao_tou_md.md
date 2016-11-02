### 固定表头
***
本节主要介绍框架的固定表头功能。
> 支持多行表头固定，调整列宽。

#### 初始化
* Data属性：table添加属性`data-toggle="tablefixed"`。

  *DOM示例代码：*
```html
<table class="table table-bordered table-hover table-striped table-top" data-toggle="tablefixed" data-height="150">
    <thead>
        <tr>
            <th rowspan="2" data-order-field="operation">ID</th>
            <th rowspan="2" data-order-field="name">姓名</th>
            <th rowspan="2" data-order-field="sex">性别</th>
            <th colspan="2" align="center">出生信息</th>
        </tr>
        <tr>
            <th data-order-field="birthday">出生日期</th>
            <th data-order-field="birthplace">出生地</th>
        </tr>
    </thead>
    <tbody>
        <tr>
            <td>1</td>
            <td>一一</td>
            <td>♂</td>
            <td>2000-01-01</td>
            <td>CN</td>
        </tr>
        ...
    </tbody>
</table>
```
* jQuery API：
      $(table).tablefixed(options)
      
#### 参数（options）


| 名称 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| nowrap | boolean | false | [可选] 禁止单元格内容自动换行。 |
| width | int/percent | 100% | [可选] 表格宽度，可设固定宽度(像素)或百分比。 |
| height | int | null | [可选] 表格高度(像素)。 |
**注意：**表格宽度(css定义的宽度)超出页片的宽度将出现`横向滚动条`，普通表格也适用。


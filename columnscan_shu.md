### datagrid columns参数
***
本节介绍datagrid组件中列模型columns的对象参数。
#### columns 对象参数
* 用HTML表头初始化为datagrid的，通过th的`data-options`属性定义columns对象参数。
* 凡是含有*`F`*标记的参数对于多表头均无效。
* 凡是含有*`D<`*标记的参数对于HTML表头均无效。

| 名称 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| name | string | null | [可选] *`F`* 该列字段名(关联json数据、xml数据、编辑及保存的数据)。`未设置name将不能进行添加\编辑等操作` |
| label | string | null | [可选] <span class="badge"><i>D</i></span> 显示的列标题。 |
| width | int | 50或HTML表格对应列的宽 | [可选] 列宽。 |
| align | string | left | [可选] 对齐方式(left、center、right)。 |
| type | string | string | [可选] *`F`* 数据类型(string、boolean、select、textarea、date、lookup、spinner)。 |
| align | string | left | [可选] 对齐方式(left、center、right)。 |
| add | boolean | true | [可选] *`F`* 允许该列添加数据。 |
| edit | boolean | true | [可选] *`F<`* 允许该列编辑数据。 |
| attrs | object | null  | [可选] *`F`* 编辑时，表单域的附加参数。示例：`{readonly:'readonly'}` |
| rule | string | null | [可选] *`F`* 编辑时，表单域名的验证规则。示例：`required;length(6)` |
| items | array/function | null | [可选] *`F`* 用于数据渲染或筛选\编辑时的select填充。<br />array示例：`[{'true':'男'}, {'false':'女'}],`<br />function示例：`function() {return $.getJSON('/datagrid/demo-items-state.js')}` |
| render | function(value) | null | [可选] *`F`* 将列数据渲染成其他样式，方法参数value为datagrid数据提供的原始值。不显示空值示例：`function(value){return !value `&#124;&#124;`  value == 'null' ? '' : value}`，datagrid提供基于items的默认渲染：`$.datagrid.renderItem` |
| pattern | string | null | [可选] *`F`* 配合type='date'使用，设置日期格式。示例：`yyyy-MM-dd HH:mm` |
| calc | string | null | [可选] *`F`* 列统计，可选(count、sum、avg、min、max)。 |
| calcTit | string | null | [可选] *`F`* 列统计说明，对应calc(总数、合计、平均、最小、最大)。 |
| calcDecimal | int | 2 | [可选] *`F`* 列统计数据保留小数点位数。 |
| hide | boolean | false | [可选] *`F`* 是否隐藏该列。 |
| menu | boolean | true | [可选] *`F<`* 列上是否出现菜单按钮（对于多表头，仅对字段列有效）。 |
| lock | boolean | false | [可选] *`F`* 是否锁定该列(尽量不用，影响速度)。 |
| quicksort | boolean | true | [可选] *`F<`* 允许点击该列进行快速排序。 |
#### 示例代码
* 简单列模型
```js
[
      {
          name: 'operation',
          label: '类型',
          type : 'select',
          items: [{'01':'神话'}, {'02':'传说'}, {'03':'漫画'}, {'04':'历史'}, {'05':'其他'}],
          align: 'center',
          width: 80,
          render: $.datagrid.renderItem
      },
      {
          name: 'name',
          label: '姓名',
          align: 'center',
          width: 100,
          rule: 'required'
      },
      {
          name: 'sex',
          label: '性别',
          type: 'select',
          items: [{'true':'男'}, {'false':'女'}],
          align: 'center',
          width: 40,
          render: $.datagrid.renderItem
      }
  ]
```
* 多表头模型
```js
[
      {
          name: 'operation',
          label: '类型',
          type : 'select',
          items: [{'01':'神话'}, {'02':'传说'}, {'03':'漫画'}, {'04':'历史'}, {'05':'其他'}],
          align: 'center',
          width: 80,
          render: $.datagrid.renderItem
      },
      {
          name: 'name',
          label: '姓名',
          align: 'center',
          width: 100,
          rule: 'required'
      },
      {
          label: '拼音姓名',
          columns: [{
              name: 'firstname',
              label: '拼音姓',
              width: 80
          },{
              name: 'lastname',
              label: '拼音名',
              width: 80,
              hide : true
          }]
      },
      {
          name: 'sex',
          label: '性别',
          type: 'select',
          items: [{'true':'男'}, {'false':'女'}],
          align: 'center',
          width: 40,
          render: $.datagrid.renderItem
      }
  ]
```
* HTML简单表头
```js
<thead>
    <tr>
        <th data-options="{
            name:'operation',
            items: [{'01':'神话'}, {'02':'传说'}, {'03':'漫画'}, {'04':'历史'}, {'05':'其他'}],
            render: $.datagrid.renderItem,
            type:'select'}">类型</th>
        <th data-options="{name:'name'}">姓名</th>
        <th data-options="{name:'sex', items: [{'true':'男'}, {'false':'女'}],
            render: $.datagrid.renderItem, type:'select'}">性别</th>
    </tr>
</thead>
```
* HTML多表头
```js
<thead>
    <tr>
        <th rowspan="2" data-options="{name:'operation',
            items: [{'01':'神话'}, {'02':'传说'}, {'03':'漫画'}, {'04':'历史'}, {'05':'其他'}],
            render: $.datagrid.renderItem, type:'select'}">类型</th>
        <th rowspan="2" data-options="{name:'name'}">姓名</th>
        <th colspan="2">拼音姓名</th>
        <th rowspan="2" data-options="{name:'sex', items: [{'true':'男'}, {'false':'女'}],
            render: $.datagrid.renderItem, type:'select'}">性别</th>
    </tr>
    <tr>
        <th data-options="{name:'firstname'}">拼音姓</th>
        <th data-options="{name:'lastname'}">拼音名</th>
    </tr>
</thead>
```

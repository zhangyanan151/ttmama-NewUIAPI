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
                </tr>
                <tr>
                    | align |
                    | string |
                    | left |
                    | [可选] 对齐方式(left、center、right)。 |
                </tr>
                <tr>
                    | add |
                    | boolean |
                    | true |
                    | [可选] <span class="badge"><i>F</i></span> 允许该列添加数据。 |
                </tr>
                <tr>
                    | edit |
                    | boolean |
                    | true |
                    | [可选] <span class="badge"><i>F</i></span> 允许该列编辑数据。 |
                </tr>
                <tr>
                    | attrs |
                    | object |
                    | null |
                    | [可选] <span class="badge"><i>F</i></span> 编辑时，表单域的附加参数。示例：`{readonly:'readonly'}` |
                </tr>
                <tr>
                    | rule |
                    | string |
                    | null |
                    | [可选] <span class="badge"><i>F</i></span> 编辑时，表单域名的验证规则。示例：`required;length(6)` |
                </tr>
                <tr>
                    | items |
                    | array/function |
                    | null |
                    | [可选] <span class="badge"><i>F</i></span> 用于数据渲染或筛选\编辑时的select填充。array示例：`[{'true':'男'}, {'false':'女'}],`，function示例：`function() {return $.getJSON('/datagrid/demo-items-state.js')}` |
                </tr>
                <tr>
                    | render |
                    | function(value) |
                    | null |
                    | [可选] <span class="badge"><i>F</i></span> 将列数据渲染成其他样式，方法参数value为datagrid数据提供的原始值。不显示空值示例：`function(value){return !value || value == 'null' ? '' : value}`，datagrid提供基于items的默认渲染：`$.datagrid.renderItem` |
                </tr>
                <tr>
                    | pattern |
                    | string |
                    | null |
                    | [可选] <span class="badge"><i>F</i></span> 配合type='date'使用，设置日期格式。示例：`yyyy-MM-dd HH:mm` |
                </tr>
                <tr>
                    | calc |
                    | string |
                    | null |
                    | [可选] <span class="badge"><i>F</i></span> 列统计，可选(count、sum、avg、min、max)。 |
                </tr>
                <tr>
                    | calcTit |
                    | string |
                    | null |
                    | [可选] <span class="badge"><i>F</i></span> 列统计说明，对应calc(总数、合计、平均、最小、最大)。 |
                </tr>
                <tr>
                    | calcDecimal |
                    | int |
                    | 2 |
                    | [可选] <span class="badge"><i>F</i></span> 列统计数据保留小数点位数。 |
                </tr>
                <tr>
                    | hide |
                    | boolean |
                    | false |
                    | [可选] <span class="badge"><i>F</i></span> 是否隐藏该列。 |
                </tr>
                <tr>
                    | menu |
                    | boolean |
                    | true |
                    | [可选] <span class="badge"><i>F</i></span> 列上是否出现菜单按钮（对于多表头，仅对字段列有效）。 |
                </tr>
                <tr>
                    | lock |
                    | boolean |
                    | false |
                    | [可选] <span class="badge"><i>F</i></span> 是否锁定该列(尽量不用，影响速度)。 |
                </tr>
                <tr>
                    | quicksort |
                    | boolean |
                    | true |
                    | [可选] <span class="badge"><i>F</i></span> 允许点击该列进行快速排序。 |
                </tr>
            </tbody>
        </table>
        

<h4>示例代码</h4>
        <ul class="nav nav-tabs" role="tablist" style="margin:0;">
            <li class="active"><a href="#datagrid-columns-demo1" role="tab" data-toggle="tab">简单列模型</a></li>
            <li><a href="#datagrid-columns-demo2" role="tab" data-toggle="tab">多表头模型</a></li>
            <li><a href="#datagrid-columns-demo3" role="tab" data-toggle="tab">HTML简单表头</a></li>
            <li><a href="#datagrid-columns-demo4" role="tab" data-toggle="tab">HTML多表头</a></li>
        </ul>
        <div class="tab-content">
            <div class="tab-pane fade active in" id="datagrid-columns-demo1">
                <pre class="brush: js; html-script: true">
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
                </pre>
            </div>
            <div class="tab-pane fade" id="datagrid-columns-demo2">
                <pre class="brush: js; html-script: true">
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
                </pre>
            </div>
            <div class="tab-pane fade" id="datagrid-columns-demo3">
                <pre class="brush: html">
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
                </pre>
            </div>
            <div class="tab-pane fade" id="datagrid-columns-demo4">
                <pre class="brush: html">
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
                </pre>
            </div>
        </div>
    </div>
</div>
<div class="bjui-pageFooter">
    <ul>
        <li><button type="button" class="btn-close" data-icon="close">关闭</button></li>
    </ul>
</div>


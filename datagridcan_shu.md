### datagrid参数及方法
***
本节介绍datagrid组件的参数及方法。
#### 参数（options）
* DOM方式初始化datagrid的，推荐使用集合属性`data-options`定义参数，如果使用`data属性`定义参数，注意转换成对应的名称，参见[data属性]()一节。

| 名称 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| gridTitle | string | null | [可选] 标题。 |
| columns | array | null | [可选] 表头模型，适用动态生成表头，如果未设置本参数，将自动转化静态表头为模型。<a href="doc/datagrid/datagrid-columns.html" data-toggle="navtab" data-options="{id:'doc-datagrid-columns', title:'columns参数'}">点此查看columns对象的详细参数</a> |
| data | array | null | [可选] 提供datagrid需要的数据，如果同时设置有`dataUrl`参数，本参数优先级高。 |
| dataUrl | string | null | [可选] Ajax请求数据的URL。返回数据模板:<br />**JSON:**`{total:50, pageCurrent:1, list:[{name:'孙悟空',sex:true}, {name:'美国队长', true}]}<br />**Array:**`{total:50, pageCurrent:1, list:[['孙悟空',true], ['美国队长', true]]}`    
                     |
                </tr>
                <tr>
                    | loadType |
                    | string |
                    | POST |
                    | [可选] Ajax请求方式。 |
                </tr>
                <tr>
                    | dataType |
                    | string |
                    | json |
                    | [可选] 数据类型，可选参数['json' | 'array' | 'xml']。 |
                </tr>
                <tr>
                    | hiddenFields |
                    | array |
                    | null |
                    | [可选] `仅用于dataType='array'时`隐藏字段，可以将不能加载到页面上的值设置到给定的字段，array数据除去表头的列后依次赋值。 |
                </tr>
                <tr>
                    | local |
                    | string |
                    | remote |
                    | [可选] 处理数据方式，可选参数['local' | 'remote']，(影响（分页、排序、筛选）)。 |
                </tr>
                <tr>
                    | fieldSortable |
                    | boolean |
                    | true |
                    | [可选] 点击页头字段快速排序。`普通表格转为datagrid的，需设置dataUrl参数，local = 'remote'` |
                </tr>
                <tr>
                    | filterThead |
                    | boolean |
                    | true |
                    | [可选] 允许表格头部快速筛选。`普通表格转为datagrid的，需设置dataUrl参数，local = 'remote'` |
                </tr>
                <tr>
                    | sortAll |
                    | boolean |
                    | false |
                    | [可选] 排序范围，true = 所有数据排序， false = 当前页数据排序。`普通表格转为datagrid的，默认为true` |
                </tr>
                <tr>
                    | filterAll |
                    | boolean |
                    | false |
                    | [可选] 筛选范围，true = 从所有数据中筛选，false = 从当前页数据中筛选。`普通表格转为datagrid的，默认为true` |
                </tr>
                <tr>
                    | filterMult |
                    | boolean |
                    | true |
                    | [可选] 支持多字段筛选。 |
                </tr>
                <tr>
                    | linenumberAll |
                    | boolean |
                    | false |
                    | [可选] 行号范围，true = 为所有数据编号，false = 为当前页数据编号。 |
                </tr>
                <tr>
                    | showLinenumber |
                    | boolean/string |
                    | true |
                    | [可选] 是否显示行号，参数[true | false | 'lock']，lock参数 = 锁定行号列（适用于多列字段，出现横向滚动条的情况）。 |
                </tr>
                <tr>
                    | showCheckboxcol |
                    | boolean/string |
                    | false |
                    | [可选] 是否显示行复选框，参数同上。 |
                </tr>
                <tr>
                    | showEditbtnscol |
                    | boolean |
                    | false |
                    | [可选] 是否显示编辑按钮列。 |
                </tr>
                <tr>
                    | showTfoot |
                    | boolean |
                    | false |
                    | [可选] 是否显示页脚，适用于显示统计信息，需要字段相关参数支持。 |
                </tr>
                <tr>
                    | showToolbar |
                    | boolean |
                    | false |
                    | [可选] 是否显示工具条，需要设置参数`toolbarItem`或`toolbarCustom`。 |
                </tr>
                <tr>
                    | toolbarItem |
                    | string |
                    | null |
                    | [可选] 显示工具条按钮，可选参数['all, add, edit, cancel, save, del, import, export, |']，“all” = 显示所有按钮，“|” = 按钮组分隔符。 |
                </tr>
                <tr>
                    | toolbarCustom |
                    | string/object/function |
                    | null |
                    | [可选] 自定义的html内容或jQuery DOM对象，支持带返回值函数。 |
                </tr>
                <tr>
                    | columnResize |
                    | boolean |
                    | true |
                    | [可选] 允许调整列宽。 |
                </tr>
                <tr>
                    | columnMenu |
                    | boolean |
                    | true |
                    | [可选] 表头字段列上显示菜单按钮。 |
                </tr>
                <tr>
                    | columnShowhide |
                    | boolean |
                    | true |
                    | [可选] 表头字段列菜单上出现 “显示/隐藏 列” 选项。 |
                </tr>
                <tr>
                    | columnFilter |
                    | boolean |
                    | true |
                    | [可选] 表头字段列菜单上出现 “过滤” 选项。 |
                </tr>
                <tr>
                    | columnLock |
                    | boolean |
                    | true |
                    | [可选] 表头字段列菜单上出现 “锁定列、解除锁定” 选项。 |
                </tr>
                <tr>
                    | paging |
                    | boolean/object |
                    | true |
                    | [可选] 是否显示分页组件，可设置分页参数。分页参数模板：
                        `{pageSize:30, selectPageSize:'30,60,90', pageCurrent:1, showPagenum:5, total:0}`<br>
                        `如果local='remote'，并通过dataUrl参数请求json数据时，返回的数据要提供total、pageCurrent参数，可提供pageSize参数`
                     |
                </tr>
                <tr>
                    | pagingAlign |
                    | string |
                    | center |
                    | [可选] 分页组件对齐方式，参数['left' | 'center' | 'right'] |
                </tr>
                <tr>
                    | editUrl |
                    | string |
                    | null |
                    | [可选] 保存编辑、添加数据的url，Ajax请求方式为POST，服务器端接收的参数名称为"json"，数据类型是JSON Array。 |
                </tr>
                <tr>
                    | editCallback |
                    | function(json) |
                    | null |
                    | [可选] 保存成功后的回调，返回的json内容可以是B-JUI默认的回调json或保存后的json数据，`datagrid默认回调：如果返回保存后的json数据，将会更新对应的数据行`。 |
                </tr>
                <tr>
                    | editMode |
                    | string |
                    | inline |
                    | [可选] 编辑、添加数据的方式，参数[false | 'inline' | 'dialog']。false = 不能编辑，inline = 行内编辑，dialog = 弹窗编辑。 |
                </tr>
                <tr>
                    | editDialogOp |
                    | object |
                    | null |
                    | [可选] 弹窗编辑方式时，设置弹出窗口的参数，如`{width:500, height:300, mask:false}` |
                </tr>
                <tr>
                    | inlineEditMult |
                    | boolean |
                    | true |
                    | [可选] 允许行内编辑模式下同时添加/编辑多行。 |
                </tr>
                <tr>
                    | saveAll |
                    | boolean |
                    | true |
                    | [可选] 适用于多行行内编辑时，一次性保存全部数据，发送到服务器端数据格式见参数`editUrl`。 |
                </tr>
                <tr>
                    | addLocation |
                    | string |
                    | first |
                    | [可选] 添加新行数据于当前页的位置，参数['first' | 'last' | 'prev' | 'next']，参数prev和next参考当前选中行位置。 |
                </tr>
                <tr>
                    | delUrl |
                    | string |
                    | null |
                    | [可选] 删除数据的url，服务器端接收的数据见参数`delPK` |
                </tr>
                <tr>
                    | delType |
                    | string |
                    | POST |
                    | [可选] Ajax删除数据的请求方式。 |
                </tr>
                <tr>
                    | delPK |
                    | string |
                    | null |
                    | [可选] 设置删除主键名，如果设置了主键，则只发送该字段的值(删除多条则主键值以逗号分隔)到服务器端，否则发送JSON数据（参数名"json"，数据类型为JSON Array）。 |
                </tr>
                <tr>
                    | delConfirm |
                    | boolean/string |
                    | null |
                    | [可选] 删除前的确认提示，参数[true | false | '自定义提示信息']，参数为false时不弹出提示信息。 |
                </tr>
                <tr>
                    | delCallback |
                    | function(json) |
                    | null |
                    | [可选] 删除成功后的回调函数，返回的json内容为B-JUI默认的回调json。 |
                </tr>
                <tr>
                    | jsonPrefix |
                    | string |
                    | null |
                    | [可选] 发送到服务器端的json数据(name)加前缀，包括(保存、删除、筛选)操作。 |
                </tr>
                <tr>
                    | contextMenuH |
                    | boolean |
                    | true |
                    | [可选] 在表头上右键点击时出现 ”显示/隐藏列“ 的快捷菜单。 |
                </tr>
                <tr>
                    | contextMenuB |
                    | boolean |
                    | false |
                    | [可选] 在数据行右键点击时出现快捷菜单，菜单选项有(刷新、添加、编辑、取消、删除)。 |
                </tr>
                <tr>
                    | hScrollbar |
                    | boolean |
                    | false |
                    | [可选] 允许出现横向滚动条。 |
                </tr>
                <tr>
                    | fullGrid |
                    | boolean |
                    | false |
                    | [可选] 使表格铺满网格容器(如果值为true，则需要设置有列宽，并且总宽度小于datagrid容器宽度时有效)。 |
                </tr>
                <tr>
                    | width |
                    | int/percent |
                    | null |
                    | [可选] datagrid容器宽度，默认为父容器的宽，相当于'100%'。 |
                </tr>
                <tr>
                    | height |
                    | int/percent |
                    | 300 |
                    | [可选] datagrid容器高度。 |
                </tr>
                <tr>
                    | importOption |
                    | object |
                    | null |
                    | [可选] 工具栏的导入按钮参数，dialog或navtab方式打开导入页面，参数模板`{type:"dialog", options:{url:'', width:400, height:200}}` |
                </tr>
                <tr>
                    | exportOption |
                    | object |
                    | null |
                    | [可选] 工具栏的导出按钮参数，执行ajax url或以dialog or navtab方式打开导出页面，参数模板`{type:"ajax", options:{url:""}}` |
                </tr>
                <tr>
                    | beforeEdit |
                    | function |
                    | null |
                    | [可选] 带返回值方法，编辑数据前调用，返回true继续编辑，返回false取消编辑。 |
                </tr>
                <tr>
                    | beforeDelete |
                    | function |
                    | null |
                    | [可选] 带返回值方法，删除数据前调用，返回true继续删除，返回false取消删除。 |
                </tr>
                <tr>
                    | afterSave |
                    | function($trs, datas) |
                    | null |
                    | [可选] 保存成功后执行方法，参数$trs为保存行(jQuery 对象)，datas为保存行对应数据(JSON Array)。 |
                </tr>
                <tr>
                    | afterDelete |
                    | function |
                    | null |
                    | [可选] 删除成功后执行方法。 |
                </tr>
            </tbody>
        </table>
        <h4>方法</h4>
        <table class="table table-bordered table-striped table-hover">
            <thead>
                <tr>
                    <th>方法名</th>
                    <th>参数类型</th>
                    <th>参数说明</th>
                    <th>描述</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    | showLinenumber(flag) |
                    | boolean/string |
                    | true | false， 'lock' | 'unlock' |
                    | 行号列：显示、隐藏、锁定、解除锁定。 |
                </tr>
                <tr>
                    | showCheckboxcol(flag) |
                    | boolean/string |
                    | true | false， 'lock' | 'unlock' |
                    | 复选框列：显示、隐藏、锁定、解除锁定。 |
                </tr>
                <tr>
                    | showEditCol(tabids) |
                    | boolean |
                    | true | false |
                    | 编辑按钮列：显示、隐藏。 |
                </tr>
                <tr>
                    | showhideColumn(column, showFlag) |
                    | object/int, boolean |
                    | column = 列索引或字段列的jQuery对象，showFlag = true/false |
                    | 显示、隐藏某列。 |
                </tr>
                <tr>
                    | selectedRows(rows, [selected]) |
                    | int/string/object, [boolean] |
                    | 单个数据行的索引、逗号分隔的行索引字符串、数据行的jQuery对象，[可选参数，选中|取消选中，默认选中] |
                    | 选中/取消选中行。 |
                </tr>
                <tr>
                    | add(addLocation) |
                    | string |
                    | 'first' | 'last' | 'prev' | 'next' |
                    | 添加行，参数参考datagrid参数`addLocation`。 |
                </tr>
                <tr>
                    | doEditRow(row) |
                    | object/int |
                    | 数据行的jQuery对象或行索引。 |
                    | 编辑行。 |
                </tr>
                <tr>
                    | doCancelEditRow(row) |
                    | object/int |
                    | 数据行的jQuery对象或行索引。 |
                    | 取消编辑行。 |
                </tr>
                <tr>
                    | doSaveEditRow(row) |
                    | object/int |
                    | 数据行的jQuery对象或行索引。 |
                    | 保存编辑行。 |
                </tr>
                <tr>
                    | delRows(rows) |
                    | int/string/object |
                    | 单个数据行的索引、逗号分隔的行索引字符串、数据行的jQuery对象 |
                    | 删除行。 |
                </tr>
                <tr>
                    | saveAll() |
                    | -- |
                    | -- |
                    | 保存所有编辑行。 |
                </tr>
                <tr>
                    | refresh() |
                    | -- |
                    | -- |
                    | 刷新，重新加载数据。 |
                </tr>
                <tr>
                    | jumpPage(pageNum, [pageSize]) |
                    | int, int |
                    | 跳转页码(仅设置分页大小参数时，可设为null)，[可选参数，页大小] |
                    | 跳转到指定页码。 |
                </tr>
                <tr>
                    | destroy() |
                    | -- |
                    | -- |
                    | 销毁datagrid。 |
                </tr>
            </tbody>
        </table>
        <h4>取得选中行</h4>
        <blockquote class="point">$('table - selector').data('selectedTrs')</blockquote>
    </div>
</div>
<div class="bjui-pageFooter">
    <ul>
        <li><button type="button" class="btn-close" data-icon="close">关闭</button></li>
    </ul>
</div>


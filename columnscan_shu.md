

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


### datagrid表头顺序调整及列隐藏
***
本节介绍datagrid表头顺序的调整及列的显示隐藏。
#### 示例代码
* HTML中在datagrid的table中添加按钮

```html
 <table id="test-datagrid" data-width="100%" data-height="500" class="table table-bordered">
     <div class="datagrid-make-btn">
         <button type="button" data-target="#doc-dialog-target" class="dropdown-toggle" data-            toggle="dialog" data-width="320" data-height=" 460" data-id="dialog-table-head" data-mask="true" data-title="配置列表项" data-maxable="false" data-minable="false" data-resizable="true" data-on-load="doc_dialog_onLoad" data-fresh="true">
             <i class="fa fa-cog"></i>
         </button>
     </div>
 </table>
```
* HTML中添加弹出框代码

```html
<div id="doc-dialog-target" data-noinit="true" class="hide">
 <div class="bjui-pageContent" data-noinit="true">
 <ul id="table-head"></ul>
 </div>
 <div class="bjui-pageFooter table-foot">
 <button type="submit" id="tabs-submit" class="btn-default">保存</button>
 </div>
</div>
```
* 引入Sortable.js
* 添加JS代码

```js
//弹出框加载前根据列名生成选项
$(document).on('bjui.beforeLoadDialog', function(e) {
 var $dialog = $(e.target);
 var datagrid = $("#test-datagrid").data('bjui.datagrid');
 var clumns = datagrid.columnModel;
 $("#table-head").empty();
 $.each(clumns, function(i, n) {
     if(n.name == 'gridNumber' || n.name == 'gridCheckbox' || n.name == 'gridEdit') return;
     var $li = $('<li class="table-head-h"></li>'),
     $input = $('<input type="checkbox" id="table-input-'+i+'" >'),
     $span = $('<span class="drag-handle">&#9776;</span>'),
     $label = $('<label for="table-input-'+i+'"></label>');
     $input.attr('data-options',JSON.stringify(n));
     $input.attr('checked', !n.hidden);
     $label.text(n.label);
     $span.appendTo($li);
     $input.appendTo($li);
     $label.appendTo($li);
     $li.appendTo($("#table-head"));
     })
 })

//弹出框关闭前调用的方法
function doc_dialog_beforeClose($dialog) {   
 var $tabs = $dialog.find(".table-head-h > input");
 var clumns = [];
 for(var i = 0; i<$tabs.length; i++) {
     var cl = $($tabs[i]).data('options');
     cl.index = i;
     clumns.push(cl);
 }
 $('#test-datagrid').datagrid('refreshtable', false);
 $('#test-datagrid').empty();
 $('.bjui-pageContent-table>div').append('<table id="test-datagrid" data-width="100%" data-height="500" class="table table-bordered"></table>');
 $('.bjui-datagrid').remove();
 $('#test-datagrid').datagrid({
     gridTitle : 'datagrid 完整示例',
     showToolbar: true,
     toolbarItem: 'all',
     local: 'local',
     dataUrl: 'datagrid/datagrid-demo-json.json',
     dataType: 'json',
     sortAll: true,
     filterAll: true,
     columns: clumns,
     hiddenFields: [{name:'deptcode'}],
     editUrl: 'ajaxDone1.html',
     paging: {pageSize:50, pageCurrent:10},
     showCheckboxCol: true,
     showEditBtnsCol: true,
     linenumberAll: true,
     fullGrid:true
 });
 $("#table-head").dialog('closeCurrent');
}

//弹出框加载时调用的方法
function doc_dialog_onLoad($dialog) {
     Sortable.create(document.getElementById('table-head'), {
         handle: '.drag-handle',
         animation: 150
     });
     $(".table-head-h > input").unbind('click');
     $(".table-head-h > input").bind('click',function(e) {
         var that = $(this);
         that.data("options").hide = !that.data("options").hide;
         if(!that.data("options").hide) {
             delete that.data("options").hidden;
         }
     });
     $("#tabs-submit").click(function(e){
         doc_dialog_beforeClose($(this).parent().parent().find("#table-head"));
     });
 }

```

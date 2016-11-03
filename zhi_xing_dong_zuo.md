### Ajax 动作
***
本节主要介绍框架的Ajax 动作（如：删除、导出等）。

  `DOM示例：`
* **doAjax(适用于 `删除` 等)**：

  *DOM示例代码：*
```html
<a type="button" class="btn btn-default" href="ajaxDone3.html" data-toggle="doajax" data-confirm-msg="确定要删除吗？">删除动作</a>
```
jQuery API:
```js
$(selector).bjuiajax('doAjax', options)
```
* **doExport(适用于 `导出`)**：

  *DOM示例代码：*
```html
<a type="button" class="btn btn-default" href="book1.xlsx" data-toggle="doexport" data-confirm-msg="确定要导出吗？">导出数据</a>
```
jQuery API:
```js
$(selector).bjuiajax('doExport', options)
```
* **doAjaxChecked(适用于 `选中项删除` 等)**：

  *DOM示例代码：*
```html
<a type="button" class="btn btn-default" href="ajaxDone3.html" data-toggle="doajaxchecked" data-group="delids" data-confirm-msg="确定要删除选中项吗？">批量删除动作</a>
```
jQuery API:
```js
$(selector).bjuiajax('doAjaxChecked', options)
```
* **doExportChecked(适用于 `选中项导出`)**：

  *DOM示例代码：*
```html
<a type="button" class="btn btn-default" href="ajaxDone3.html" data-toggle="doexportchecked" data-confirm-msg="确定要导出选中项吗？">批量导出</a>
 ```
jQuery API:
```js
$(selector).bjuiajax('doExportChecked', options)
```

#### 参数（options）

| 名称 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| url | string | null | [必选] *`<i>D-Url`* ajax处理的URL，a链接触发时可以将url定义在href属性。 |
| type | string | POST | [可选] ajax请求方式。(`导出类动作无效`) |
| data | object | null | [可选] ajax请求发送到服务器的数据。(`导出类动作无效`) |
| confirmMsg | string | null | [可选] 执行动作前的确认提示。 |
| callback | function(json) | null | [可选] 回调函数。 |
| loadingmask | boolean | true | [可选] ajax请求时是否显示数据加载遮罩。 |
| group | string | null | `[批量操作专用 - 必选]` 选项checkbox框的名称。 |
| idname | string | ids | `[批量操作专用 - 可选]` 发送到服务端的参数名称，发送到服务端的id值以`,`分隔。 |
**注意：**本节涉及的`selector`，请尽量使用该容器内部的元素，否则会影响默认回调函数的正确执行。


### jQuery API调用
***
本框架内置组件及部分插件都可以通过jQuery选择器进行API调用，支持链式操作，如下示例。
* 以下是示例展示打开一个ID为'mydialog'的弹出窗口，然后更改该选择器的值为'OK'：

 `API示例：`
 
  *本例的完整代码：*
```js
$('a.api-test').click(function() {
    $(this).dialog({id:'mydialog', url:'doc/base/mydialog.html', title:'测试弹窗'}).text('OK')
});
```
```html
<a href="javascript:;" class="api-test">测试API</a>
```
*jQuery API代码：*
```js
$(selector).dialog({id:'mydialog', url:'doc/base/mydialog.html', title:'测试弹窗'}).text('OK')
```
`selector`是符合jQuery规范的选择器。
#### `组件的初始化：`
本框架的内置组件通过如下方式进行初始化，以及调用开放的方法。

* `$(selector).datepicker()`：以默认值初始化（创建）一个日期选择器。**部分组件不支持默认值初始化，如`dialog\navtab`必须提供url参数**
* `$(selector).dialog({id:'mydialog', url:'mydialog.html', title:'我的弹窗标题'})`：根据参数初始化（创建）一个弹出窗口。
* `$(selector).dialog('refresh', 'mydialog')`：调用dialog组件的刷新方法`refresh`，方法名后带上相关参数。
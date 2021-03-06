### 事件
***
本框架内置组件的事件基本上都是jQuery自定义事件。
* 监听事件
```js
$(selector).on('Event name', function(e) {
    //do something...
})
```
* 触发事件
```js
$(selector).trigger('Event name')
```

#### 全局事件

| 事件名称 | 中文说明 | 描述 |
| -- | -- | -- |
| bjui.initUI | 框架初始化事件 | 监听该事件，可以为指定的DOM初始化框架组件及插件，例如：本框架监听该事件用于在文档加载完成或ajax加载完成时，初始化框架及插件 |
  | bjui.beforeInitUI | 框架初始化前事件 | 监听该事件，可以在框架初始化前进行相关操作。例如：本框架的任一容器DOM如果添加了属性`['data-noinit="true"]`，该容器内的元素都不会被初始化，处理这个流程就监听了本件事。 |
| bjui.afterInitUI | 框架初始化后事件 | 监听该事件，可以在框架初始化后进行相关操作，示例同上。 |
| bjui.ajaxStatus | ajax请求状态事件 | `框架内部事件`。本事件用于在ajax请求过程中（`ajaxStart - > ajaxStop`），显示/隐藏 框架的Mask loading效果。 |
| bjui.resizeGrid | 窗口缩放事件 | 监听该事件，可在浏览器窗口或dialog窗口缩放时进行相关操作。 |
| bjui.beforeAjaxLoad | ajax载入前事件 | 监听该事件，可在使用`ajaxUrl`方法 **(navtab/dialog均用此方法加载子页片内容)** 前进行相关操作，例如：本框架监听该事件用于在重载入子页片前释放在body中生成的selectpicker插件资源。 |
#### bjui.initUI事件示例：
1. 定义一个div容器，并为它添加一个文本框，让div容器监听bjui.initUI事件（将文本框的边框颜色改为红色）。
2. 点击"创建div容器"按钮，将div容器附加到按钮后面。
3. 点击"触发bjui.initUI事件"按钮，让div容器触发bjui.initUI事件。

**说明：**可以多次监听某一事件，jQuery会依次处理，本例触发bjui.initUI事件时会先触发框架的监听事件(`bjui-plugins.js: 为文本框添加Class[form-control]`)，再触发自定义的监听事件(`红色边框`)。

`事件示例完整代码：`
```js
var $doc_div = $('&lt;div class="doc-eventbox" style="display:inline-block; margin-left:10px;"><input type="text"></div>')
$doc_div.on('bjui.initUI', function() {
    $(this).find('input').css('border-color','red')
})
$('a.doc-event-1').click(function() {
    $doc_div.insertAfter('a.doc-event-2')
    $('a.doc-event-2').removeClass('hide')
    $(this).hide()
})
$('a.doc-event-2').click(function() {
    $(this).hide()
    $doc_div.trigger('bjui.initUI')
})
```
```html
<a href="javascript:;" class="btn btn-default doc-event-1">创建div容器</a>
<a href="javascript:;" class="btn btn-default hide doc-event-2">触发bjui.initUI事件</a>
```
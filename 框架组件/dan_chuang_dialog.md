 ### 创建dialog
***
###### 创建一个dialog有以下两种方式：
* Data属性：DOM添加属性<code>data-toggle="dialog"</code>后，单击触发。<br>
 *DOM示例1：*
 ```html
<a href="mydialog.html" data-toggle="dialog" data-id="mydialog1" data-title="我的业务弹窗1">打开dialog</a>
```
*DOM示例2：*
```html
<button type="button" class="btn-green" data-toggle="dialog" data-id="mydialog2" data-url="mydialog.html" data-title="我的业务弹窗2">打开dialog</button>
```
*DOM示例3(参数集合)：*
```html
<button type="button" class="btn-green" data-toggle="dialog" data-options="{id:'mydialog2', url:'doc/dialog/mydialog.html', title:'我的业务弹窗2(参数集合)'}">打开dialog(参数集合)</button>
```
*其他示例[加载容器中的内容]：*
```html
<button type="button" class="btn-green" data-toggle="dialog" data-id="mydialog3" data-target="#doc-dialog-target" data-title="加载容器中的内容">打开dialog</button>
<div id="doc-dialog-target" data-noinit="true" class="hide">
  <p><input type="checkbox" id="doc-dialog-checkbox" data-toggle="icheck" data-label="测试Checkbox"></p>
  <p><label>文本框：</label><input type="text" placeholder="文本框1" size="25"></p>
  <p><label>下拉框：</label><select data-toggle="selectpicker"><option value="1">选项一</option><option value="2">选项二</option></select></p>
</div>
```
*其他示例[回调函数]：*
      <script type="text/javascript">
        function doc_dialog_onLoad($dialog) {
            $dialog.alertmsg('info', 'onLoad回调：不填写工号是不能关闭本弹窗的。')
        }
        function doc_dialog_beforeClose($dialog) {
            var code = $dialog.find('#doc-dialog-code').val()

            if (code) return true
            $dialog.alertmsg('error', 'beforeClose回调：关闭弹窗前请先填入你的工号。')
            return false
        }
        function doc_dialog_onClose() {
            $(this).alertmsg('info', 'onClose回调：你刚刚关闭了一个dialog。')
        }
       </script>
       <button type="button" class="btn-green" data-toggle="dialog" data-id="mydialog4" data-target="#doc-dialog-target-callback" data-title="回调函数示例" data-on-load="doc_dialog_onLoad" data-before-close="doc_dialog_beforeClose" data-on-close="doc_dialog_onClose">打开dialog</button>
        <div id="doc-dialog-target-callback" data-noinit="true" class="hide">
            <div class="text-center">
                <h3>dialog回调函数示例</h3>
                <hr>
                <p><label>工号：</label><input type="text" name="code" id="doc-dialog-code"></p>
            </div>
        </div>
* jQuery API：

  *jQuery示例：*本例完整代码

      <script type="text/javascript">
        function openMydialog(obj) {
            $(obj).dialog({id:'mydialog', url:'doc/dialog/mydialog.html', title:'我的业务弹窗'});
        }
      </script>
      <button type="button" class="btn-default" onclick="openMydialog(this)">打开dialog</button>
*jQuery方法代码：*

      $(selector).dialog(options)
**取得当前dialog的容器**：`$.CurrentDialog`

### dialog参数、方法及事件
***
* 本节介绍dialog组件的参数、方法及事件。
#### 参数（options）
* DOM方式初始化dialog的，推荐使用集合属性`data-options`定义参数，如果使用`data属性`定义参数，注意转换成对应的名称，参见[data属性](../datashu_xing.md)一节。

| 名称 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| id | string | dialog | [必选] 弹窗的ID，如果指定重复，将覆盖现有的ID相同弹窗。 |
| title | string | New Dialog | [可选] 弹窗打开后显示的名称，可从data-title属性获取或直接获取触发DOM的text值。 |
| url | string | undefined | [可选] <code>url参数或target参数必选一项</code> <span class="badge"><i>D-Url</i></span> 请求数据的url，a链接触发时可以将url定义在href属性。 |
| type | string | GET | [可选] Http请求方式，可选‘GET/POST’。 |
| data | object | {} | [可选] 请求url时，需要发送的data数据。 |
| loadingmask | boolean | true | [可选] ajax请求时是否显示数据加载遮罩。 |
| width | int | 500 | [可选] 弹窗的宽度。 |
| height | int | 300 | [可选] 弹窗的高度。 |
| max | boolean | false | [可选] 打开弹窗时直接最大化。 |
| mask | boolean | false | [可选] 是否模态窗口。 |
| resizable | boolean | true | [可选] 可以调整弹窗的大小。 |
| drawable | boolean | true | [可选] 可以拖动弹窗。 |
| maxable | boolean | true | [可选] 是否显示最大化按钮。 |
| minable | minable | true | [可选] 是否显示最小化按钮（模态弹窗无效）。 |
| target | selector | null | [可选] 从指定的jQuery容器中加载内容到dialog，请为该容器添加属性`data-noinit="true"`以阻止容器中的内容提前初始化，为容器添加Class[`hide`]以隐藏待加载内容。 |
| fresh | boolean | false | [可选] 是否保持该dialog的新生状态，表现在重复打开该dialog时，是否重新载入内容。 |
| reloadWarn | string | null | [可选] 当准备在已存在的dialog上加载内容时的确认提示信息。 |
| onLoad | function($dialog) | null | [可选] dialog加载完成后的事件回调，回调函数的参数<code>$dialog</code>为该dialog的jQuery对象。 |
| beforeClose | function($dialog) | null | [可选] <b>返回值: boolean</b>。 dialog关闭前的事件回调，返回true则关闭，返回false不关闭。 |
| onClose | function() | null | [可选] dialog关闭后的事件回调。 |
#### 方法

| 方法名 | 参数类型 | 参数说明 | 描述 |
| -- | -- | -- | -- |
| switchDialog | string | dialog ID | 切换到某个弹窗(模态弹窗无效)。 |
| refresh(id) | string | dialog ID | 刷新某个弹窗。 |
| reloadFlag(tabids) | string | 一个或多个标签ID，多个ID以`,`分隔 | 为某(几)个标签设定重载标记(当切换到该标签时重新载入)。 |
| reload(options) | object | 同dialog默认参数 | 重新载入某个弹窗，如果未指定ID，则默认重载入当前弹窗。 |
| close(id) | string | dialog ID | 关闭某个弹窗。 |
| closeCurrent() | -- | -- | 关闭当前弹窗。 |
#### 事件

| 事件名称 | 中文说明 | 描述 |
| -- | -- | -- |
| bjui.beforeLoadDialog | 载入dialog内容前事件 | 监听该事件，可以在载入dialog内容前进行相关操作。 |
| bjui.beforeCloseDialog | 关闭dialog前事件 | 监听该事件，可以在关闭dialog前进行相关操作。 |
* 这样监听dialog的事件：
      $(document).on('bjui.beforeLoadDialog', function(e) {
          var $dialog = $(e.target)
          // do something...
      })

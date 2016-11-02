### 创建navtab
***
###### 创建一个navtab有以下两种方式：
* Data属性：DOM添加属性`data-toggle="navtab"`后，单击触发。

  *DOM示例1：*
  ```html
<a href="mytab.html?d=1" data-toggle="navtab" data-id="mynavtab" data-reload-warn="已打开业务页面，确认将重新载入?" data-title="我的业务页面">打开navtab</a>
```
  *DOM示例2：*
  ```html
<button type="button" class="btn-green" data-toggle="navtab" data-id="mynavtab" data-reload-warn="已打开业务页面，确认将重新载入?" data-url="doc/navtab/mytab.html?d=2" data-title="我的业务页面">打开navtab</button>
```
  *DOM示例3(参数集合)：*
  ```html
<button type="button" class="btn-green" data-toggle="navtab" data-options="{id:'mynavtab', reloadWarn:'已打开业务页面，确认将重新载入?', url:'doc/navtab/mytab.html?d=5', title:'我的业务页面(参数集合写法)'}">打开navtab(参数集合)</button>
```
  *其他示例[回调函数]：*
```js
function doc_navtab_beforeClose($navtab) {
    var code = $navtab.find('#doc-mytab-code').val()

    if (code) return true
    $navtab.alertmsg('error', '关闭navtab前请先填入你的工号。')
    return false
}
function doc_navtab_onClose() {
    $(this).alertmsg('info', '你刚刚关闭了一个navtab。')
}
```
```html
<button type="button" class="btn-green" data-toggle="navtab" data-id="mynavtab" data-reload-warn="已打开业务页面，确认将重新载入?" data-url="doc/navtab/mytab.html?d=3" data-title="navtab回调函数示例" data-before-close="doc_navtab_beforeClose" data-on-close="doc_navtab_onClose">打开navtab</button>
```
* jQuery API：

  *jQuery示例：* 完整代码如下
```js
function openMytab(obj) {
    $(obj).navtab({id:'mynavtab', url:'doc/navtab/mytab.html', title:'我的业务页面'});
}
```
```html
<button type="button" class="btn-default" onclick="openMytab(this)">打开navtab</button>
```
* jQuery API代码：
      $(selector).navtab(options)
**说明**
  1. 取得当前navtab的内容容器：`$.CurrentNavtab`
  2. 创建已存在相同ID的navtab时，如果url一致(未设置`fresh`参数时)，默认会直接切换到该navtab，否则覆盖已存在的navtab，可以增加`reloadWarn`参数以获得警告提醒

### navtab参数、方法及事件
***
* 本节介绍navtab组件的参数、方法及事件。
#### 参数（options）
* DOM方式初始化navtab的，推荐使用集合属性`data-options`定义参数，如果使用`data属性`定义参数，注意转换成对应的名称，参见[data属性](../datashu_xing.md)一节。

| 名称 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| id | string | undefined | [必选] 标签的ID，如果指定重复，将覆盖现有的ID相同标签。 |
| title | string | New tab | [可选] 标签打开后显示的名称。 |
| url | string | undefined | [必选] <span class="badge"><i>D-Url</i></span> 请求数据的url，a链接触发时可以将url定义在href属性。 |
| external | boolean | false | [可选] 是否以iframe方式加载外部页面。 |
| type | string | GET | [可选] Http请求方式，可选‘GET/POST’。 |
| data | object | {} | [可选] 请求url时，需要发送的data数据。 |
| loadingmask | boolean | true | [可选] ajax请求时是否显示数据加载遮罩。 |
| fresh | boolean | false | [可选] 是否保持该navtab的新生状态，表现在重复打开该navtab时，是否重新载入内容。 |
| reloadWarn | string | null |[可选] 当准备在已存在的navtab上加载内容时的确认提示信息。 |
| autorefresh | boolean/int(秒) | false | [可选] 指定该navtab是否可自动刷新，为true时默认间隔15秒自动刷新，指定具体的秒数则以指定的间隔秒值自动刷新。 |
| onLoad | function($navtab) | null | [可选] navtab加载完成后的事件回调，回调函数的参数<code>$navtab</code>为该navtab内容区的jQuery对象。 |
| beforeClose | function($navtab) | null | [可选] <b>返回值: boolean</b>。 navtab关闭前的事件回调，返回true则关闭，返回false不关闭。 |
| onClose | function | null | [可选] navtab关闭后的事件回调。 |
#### 方法
| 方法名 | 参数类型 | 参数说明 | 描述 |
| -- | -- | -- | -- |
| switchTab(tabid) | string | 标签ID | 切换到某个标签。 |
| refresh(tabid) | string | 标签ID，<code>ID为空</code>则刷新当前标签 | 刷新某个标签。 |
| reloadFlag(tabids) | string | 一个或多个标签ID，多个ID以<code>,</code>分隔 | 为某(几)个标签设定重载标记(当切换到该标签时重新载入)。 |
| reload(options) | object | 同navtab默认参数 | 重新载入某个标签，如果未指定ID，则默认重载入当前标签。 |
| closeTab(tabid) | string | 标签ID | 关闭某个标签。 |
| closeCurrentTab([tabid]) | string | 标签ID，可选。 | 关闭当前标签。 |
| closeAllTab() | -- | -- | 关闭所有标签。 |
#### 事件
| 事件名称 | 中文说明 | 描述 |
| -- | -- | -- |
| bjui.beforeLoadNavtab | 载入navtab内容前事件 | 监听该事件，可以在载入navtab内容前进行相关操作。 |
| bjui.beforeCloseNavtab | 关闭navtab前事件 | 监听该事件，可以在关闭navtab前进行相关操作。 |
* 这样监听navtab的事件：
      $(document).on('bjui.beforeLoadNavtab', function(e) {
          var $navtab = $(e.target)
          // do something...
      })


### Ajax加载DOM，局部刷新
***
本节主要介绍框架的Ajax加载DOM及局部刷新。
**说明：**框架会为局部刷新的容器添加class [ `bjui-layout` ]以保证刷新DIV时不影响其他内容。
#### 初始化
* Data属性：元素添加属性`data-toggle="ajaxload"`后，单击触发 **或** 容器(如：div)添加属性`data-toggle="autoajaxload"`后，自动加载url指定的内容。

  *DOM示例代码* -- **单击加载**：
```html
<a href="doc/ajax/mylayout.html" class="btn btn-default" data-toggle="ajaxload" data-target="#myLoadDiv1">单击加载内容</a>
<div id="myLoadDiv1"></div>
```
*示例代码* -- **自动加载**：
```html
<div id="myLoadDiv2" data-toggle="autoajaxload" data-url="doc/ajax/mylayout.html"></div>
```
* Data属性：元素添加属性`data-toggle="refreshlayout"`后，单击可以刷新指定容器。

  *示例代码* -- **单击刷新**：
```html
<button type="button" class="btn-default" data-toggle="refreshlayout" data-target="#myLoadDiv1">刷新DIV</button>
```
* jQuery API：

**加载：**
```js
$(selector).bjuiajax('doLoad', options)
```
**刷新：**
```js
$(selector).bjuiajax('refreshLayout', options)
```
**刷新指定ID的div容器`多个id以** , **分隔`：**
```js
$(selector).bjuiajax('refreshDiv', divid)
```
#### 参数（options）

| 名称 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| target | selector | null | [必选] 目标容器的 `jQuery选择器表达式` 或 `DOM对象`。 |
| url | string | null | [必选] *`D-Url`* 远程加载的URL，a链接触发时可以将url定义在href属性。 |
| type | string | GET | [可选] ajax请求方式。 |
| data | object | null | [可选] ajax请求发送到服务器的数据。 |
| loadingmask | boolean | true | [可选] ajax请求时是否显示数据加载遮罩。 |
| autorefresh | boolean/int(秒) | false | [可选] 指定该div容器是否可自动刷新，为true时默认间隔15秒自动刷新，指定具体的秒数则以指定的间隔秒值自动刷新。 |


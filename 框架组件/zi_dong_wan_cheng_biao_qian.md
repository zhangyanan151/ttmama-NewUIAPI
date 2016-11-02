### 自动完成标签
***
本节主要介绍框架的自动完成标签。
#### 初始化
* Data属性：input添加属性`data-toggle="tags"`。

  *DOM示例代码*
```html
<input type="text" name="tags" value="" data-toggle="tags" data-url="ajaxTags.html" data-width="360" size="15" placeholder="输入关键字，回车提交">
```
* jQuery API：
      $(input).tags(options)

#### 参数（options）

| 名称 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| url | string | null | [必选] *`D-Url`*Ajax加载内容的URL。 |
| type | string | GET | [可选] ajax请求方式。 |
| tagname | string | tag | [可选] 标签隐藏域的name。 |
| max | int | 0 | [可选] 允许插入几个标签，0 = 不限。 |
| clear | boolean | false | [可选] 如果ajax无返回或未在下拉菜单中选择，是否清除输入字符。 |
| lightCls | string | tags-highlight | [可选] 标签选择菜单的高亮Class。 |
| width | int | 300 | [可选] 标签区域的宽度，超过将自动换行。 |
#### 返回JSON参数(Ajax请求URL的返回JSON)

| 名称 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| value | string | null | [必选] 标签的值。 |
| label | string | null | [必选] 标签的显示名称。 |
#### 事件

| 事件名称 | 中文说明 | 描述 |
| -- | -- | -- |
| aftercreated.bjui.tags | 标签创建后的事件 | 监听该事件，可以在创建好一个标签后进行相关操作。 |
* 这样监听tags的事件：`mytags - selector`表示触发自动完成标签的input选择器
```js
$('mytags - selector').on('aftercreated.bjui.tags', function(e, data) {
    var value = data.value // 当前创建的标签值
    var item  = data.item  // 当前选定项的值(object，具体值由返回JSON决定)
    var tags  = data.tags  // 所有已生成标签的值，以英文逗号(,)分隔

    // do something...
})
```
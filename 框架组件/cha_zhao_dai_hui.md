### 查找带回
***
本节主要介绍框架的查找带回功能，流程：1. 打开一个呈现数据的弹出窗口；2. 选择一个或多个值，将值返回到触发页面对应的input；3. 关闭弹出窗口。

**`关于动态更换url：`**如果需要动态更换lookup的url，需要为lookupbtn新增属性`data-newurl`，如：
```javascript
$('input').parent().find('a.bjui-lookup').data('newurl', 'new url') //通过input框修改附加按钮的url
$('lookupbtn').data('newurl', 'new url')                            //直接修改lookup按钮的url
```
#### 初始化
* Data属性：input添加属性`data-toggle="lookup"` 或 点击含有属性`data-toggle="lookupbtn"`的元素触发。

  *DOM示例代码1：*
```html
<label>PID:</label><input type="text" name="pid" size="5">
<label>查找名称：</label><input type="text" data-toggle="lookup" data-url="doc/form/mylookup.html" name="name" size="10">
```
*DOM示例代码2：*
```html
<label>PID:</label><input type="text" name="t2.pid" size="5">
<label>查找名称：</label><input type="text" name="t2.name" size="10"> <a href="doc/form/mylookup.html" data-toggle="lookupbtn" data-group="t2">打开Lookup窗口</a>
```
* jQuery API：
```js
$(input).lookup(options)
```
  
#### 参数（options）

| 名称 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| url | string | null | [必选]*`D-Url</i>` *打开lookup的URL，a链接触发时可以将url定义在href属性。 |
| group | string | null | [可选] input的名称，适用于input名称为"aa.bb"的形式，其中 group为：`aa`。 |
| suffix | string | null | [可选] input的名称后缀，适用于input名称为"abcd[]"或"aa.bb[]"的形式，其中 suffix为：`[]`，`特别注意：`如果真实情况suffix为"[]"，请写为`" []"`，空格加"[]"，以防止被转义为空数组。 |
| id | string | lookup_dialog | [可选] 弹出窗口的id。 |
| mask | boolean | true | [可选] 是否弹出模态窗口。 |
| width | int | 600 | [可选] 弹出窗口的宽度。 |
| height | int | 400 | [可选] 弹出窗口的高度。 |
| title | string | Lookup | [可选] 弹出窗口的标题，单击触发时，如未明确定义title，将取元素的text值作为title。 |
| maxable | boolean |true | [可选] 弹出窗口可以最大化。 |
| resizable | boolean | true | [可选] 弹出窗口可以调整大小。 |
#### 事件

| 事件名称 | 中文说明 | 描述 |
| -- | -- | -- |
| afterchange.bjui.lookup | 带回值后的事件 | 监听该事件，可以在input取得返回值后进行相关操作。 |
* 这样监听lookup的事件：`mylookup - selector`表示lookup赋值了的input选择器
```js
$('mylookup - selector').on('afterchange.bjui.lookup', function(e, data) {
    var myvalue = data.value

    // do something...
})
```

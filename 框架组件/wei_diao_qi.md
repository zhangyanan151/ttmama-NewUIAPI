### 微调器
***
本节主要介绍框架的微调器。
#### 初始化
* Data属性：input添加属性`data-toggle="spinner"`。

* 示例代码：*
 ```html
<input type="text" data-toggle="spinner">
```
* jQuery API：`options可为空`
      $(input).spinner(options)

#### 参数（options）

| 名称 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| min | int | 0 | [可选] 最小值。 |
| max | int | 100 | [可选] 最大值。 |
| step | number | 1 | [可选] 步长，每次调整的值大小。 |
| decimalPlace | int | 0 | [可选] 小数位数。 |
#### 事件

| 事件名称 | 中文说明 | 描述 |
| -- | -- | -- |
| afterchange.bjui.spinner | 微调后的事件 | 监听该事件，可以在调整值后进行相关操作。 |
* 这样监听spinner的事件：`myspinner - selector`表示触发微调的input选择器
```javascript
$('myspinner - selector').on('afterchange.bjui.spinner', function(e, data) {
    var myvalue = data.value

    // do something...
})
```
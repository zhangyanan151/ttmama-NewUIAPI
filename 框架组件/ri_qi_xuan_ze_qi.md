### 日期选择器
***
本节主要介绍框架的日期选择器。
#### 初始化
* Data属性：input添加属性`data-toggle="datepicker"`。

*示例代码：*

```html
<input type="text" data-toggle="datepicker">
```
* jQuery API：`options为空时，默认初始化为当前日期`

```javascript
$(input).datepicker(options)
```
#### 参数（options）

| 名称 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| pattern | string | yyyy-MM-dd | [可选] 日期格式（y=年， M=月，d=日，H=时，m=分，s=秒）。 |
| minDate | string | 1900-01-01 | [可选] 日历范围的开始日期。支持动态格式，如`data-min-date="%y-10-%M-%d"表示将最开始日期定为比当前日期小十年`。`%y = 本年`，`%M = 本月`，`%d = 今天`。 |
| maxDate | string | 2099-12-31 | [可选] 日历范围的结束日期。支持动态格式，同上。 |
| mmStep | int | 1 | [可选] 调整时间：[分] 的步长。`日期格式包含 [m] 时有效` |
| ssStep | int | 1 | [可选] 调整时间：[秒] 的步长。`日期格式包含 [s] 时有效` |
| nobtn | boolean | false | [可选] 文本框右边是否显示日历按钮 |
| onlybtn | boolean | false | [可选] 只有点击日历按钮时才触发日期选择器 |
#### 事件

| 事件名称 | 中文说明 | 描述 |
| -- | -- | -- |
| afterchange.bjui.datepicker | 日期选择后的事件 | 监听该事件，可以在选定某个日期后进行相关操作。 |
* 这样监听datepicker的事件：`mydate - selector`表示触发日期选择的input选择器
```javascript
$('mydate - selector').on('afterchange.bjui.datepicker', function(e, data) {
    var mydate = data.value

    // do something...
})
```

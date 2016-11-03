### 第三方插件：iCheck —— 美化复选框、单选框
***
本节主要介绍表美化复选框、单选框插件 - iCheck，插件地址：[http://www.bootcss.com/p/icheck/](http://www.bootcss.com/p/icheck/)。
#### 初始化
* Data属性：checkbox或radio添加属性`data-toggle="icheck"`后即可触发，属性`data-label`可以设置显示标签，如果有ID，则点击标签可勾选。<br>
**`DOM示例代码：`**
```html
<input type="checkbox" name="doc-check1" id="doc-check1" data-toggle="icheck" data-label="我是一个复选框">
<input type="radio" name="doc-radio1" id="doc-radio1" data-toggle="icheck" data-label="单选1">
<input type="radio" name="doc-radio1" id="doc-radio2" data-toggle="icheck" data-label="单选2">
```
* jQuery API：[http://www.bootcss.com/p/icheck/](http://www.bootcss.com/p/icheck/)

#### 状态改变事件
更多事件及方法见插件官网

**`示例代码：`**
```js
$('input[name="doc-check-t"]').on('ifChanged', function(e) {
    var checked = $(this).is(':checked'), val = $(this).val()

    if (checked)
        $(this).alertmsg('info', '你选择了'+ val)
    else
        $(this).alertmsg('info', '你取消了'+ val)
})
```
```html
<input type="checkbox" name="doc-check-t" id="doc-check-t1" value="1000" data-toggle="icheck" data-label="1000">
<input type="checkbox" name="doc-check-t" id="doc-check-t2" value="2000" data-toggle="icheck" data-label="2000">
<input type="checkbox" name="doc-check-t" id="doc-check-t3" value="3000" data-toggle="icheck" data-label="3000">
<input type="checkbox" name="doc-check-t" id="doc-check-t4" value="4000" data-toggle="icheck" data-label="4000">
<input type="checkbox" name="doc-check-t" id="doc-check-t5" value="5000" data-toggle="icheck" data-label="5000">
```
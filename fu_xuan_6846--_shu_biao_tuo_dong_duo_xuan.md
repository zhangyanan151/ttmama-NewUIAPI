### 复选框--鼠标拖动多选
***
本节主要介绍拖动鼠标经过复选框，复选框多选(选中或取消选中)。
#### 初始化
* 在当前模块的td元素下增加一个遮罩层,之后的鼠标事件实际是鼠标通过此遮罩层进行操作
```js
(function addSpan(){
    var span = $("<span class='zz'></span>");
    $(".table-checkbox-td").append(span);
})();
```



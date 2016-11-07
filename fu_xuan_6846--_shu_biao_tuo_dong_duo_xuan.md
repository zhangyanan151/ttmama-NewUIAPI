### 复选框--鼠标拖动多选
***
本节主要介绍拖动鼠标经过复选框，复选框多选(选中或取消选中)。
#### 初始化
* 在当前模块的td元素下增加一个遮罩层,之后的鼠标事件实际是鼠标通过操作遮罩层从而操作复选框元素

  **`示例代码`**
```js
(function addSpan(){
    var span = $("<span class='zz'></span>");
    $(".table-checkbox-td").append(span);
})();
```
```css
    .table-checkbox-td {
        position: relative;
    }
    .zz {
        position: absolute;
        top: 0;
        left: 0;
        display: inline-block;
        width: 100%;
        height: 100%;
    }
```

#### 鼠标按下和拖拽事件
* **`示例代码`**
```js
$("#bjui-navtab").delegate(".table-checkbox-td .zz","mousedown",function(ev){
    $("#bjui-navtab").css("-webkit-user-select","none");
    //样式（toggleClass）与实质(toggleiCheck)的一致
    $(this).prev(".icheckbox_minimal-purple").toggleClass("checked").children("input").iCheck('toggle');
    $(this).on("mouseup",function(){
        $(".table-checkbox-td .zz").off("mouseenter");
        return;
    });
    //（鼠标按下后，）鼠标经过时批量选中或取消选中，跟随第一个的选择
    var isCheck = $(this).prev(".icheckbox_minimal-purple").hasClass("checked");
    $(".table-checkbox-td .zz").on("mouseenter",function(){
        if(isCheck){
            $(this).prev(".icheckbox_minimal-purple").addClass("checked").children("input").iCheck('check');
        }else {
            $(this).prev(".icheckbox_minimal-purple").removeClass("checked").children("input").iCheck('uncheck');
        }

        $(window).on("mouseup",function(){
            $(".table-checkbox-td .zz").off("mouseenter");
        });
    });
});
```




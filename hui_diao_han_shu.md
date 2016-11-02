### Ajax回调函数
***
本节主要介绍框架的Ajax回调函数。

**注意：**自定义函数参数为：callback，通过DOM附加：`data-callback="自定义函数名称"`，自定义函数名称不带括号及参数。
* 自定义回调函数示例：
```javascript
function mycallback(json) {
    $(this)
        .bjuiajax('ajaxDone', json)       // 信息提示
        .navtab('refresh')                // 刷新当前navtab
        .navtab('reloadFlag', json.tabid) // 为指定的tabid设置刷新标记
    
    //do other something...
}
```
#### JSON参数

| 名称 | 类型 | 描述 |
| -- | -- | -- |
| statusCode | int | **必选。**状态码(ok = 200, error = 300, timeout = 301)，可以在BJUI.init时配置三个参数的默认值。 |
| message | string | 可选。信息内容。 |
| tabid | string | 可选。待刷新navtab id，多个id以英文逗号分隔开，当前的navtab id不需要填写，填写后可能会导致当前navtab重复刷新。 |
| dialogid | string | 可选。待刷新dialog id，多个id以英文逗号分隔开，请不要填写当前的dialog id，**要控制刷新当前dialog，请设置dialog中表单的reload参数。** |
| divid | string | 可选。待刷新div id，多个id以英文逗号分隔开，请不要填写当前的div id，**要控制刷新当前div，请设置该div中表单的reload参数。** |
| closeCurrent | boolean | 可选。是否关闭当前窗口(navtab或dialog)。 |
| forward | string | 可选。跳转到某个url。 |
| forwardConfirm | string | 可选。跳转url前的确认提示信息。 |


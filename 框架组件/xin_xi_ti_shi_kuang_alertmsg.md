### 信息提示框 alertmsg
***
本节主要介绍框架的信息提示框及相关参数。
#### 初始化
* Data属性：DOM添加属性`data-toggle="alertmsg"`，并定义type及msg参数。

 *DOM示例1：*
      <button type="button" class="btn-default" data-toggle="alertmsg" data-msg="我是一个信息提示" data-type="info">我是信息提示</button>
*DOM示例2(集合参数)：*
      <button type="button" class="btn-default" data-toggle="alertmsg" data-options="{msg:'我是错误提示', type:'error'}">我是错误提示&lt;/button>
* jQuery API：

  *示例代码：*
      <script type="text/javascript">
          $('#doc-alertmsg-demo').click(function() {
              $(this).alertmsg('confirm', '我是提示内容', {displayMode:'slide', displayPosition:'bottomcenter', okName:'Yes', cancelName:'no', title:'我是提示标题'})
          })
      </script>
      <a href="javascript:;" id="doc-alertmsg-demo">测试提示框</a>
 *API调用方法：*
      $(selector).alertmsg(type, msg, options)
#### 参数（options）
* DOM方式初始化datagrid的，推荐使用集合属性`data-options`定义参数，如果使用`data属性`定义参数，注意转换成对应的名称，参见[data属性](../datashu_xing.md)一节。
* 参数`displayPosition`、`displayMode`、`closeTimer`有可以在框架初始化时进行全局设置，参考[框架初始化](../kuang_jia_chu_shi_hua.md)

| 名称 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| type | string | null | [必选] 信息提示方式，参数有['ok' 、 'correct' 、 'info' 、 'warn'  、 'error'  、 'confirm'] ，其中ok为correct的别名，confirm为确认提示框。 |
| msg | string | null | [必选] 提示的内容。 |
| displayPosition | string | topcenter | [可选] 提示框显示位置，参数有['topleft'、 'topcenter' 、 'topright' 、 'middleleft' 、 'middlecenter' 、 'middleright' 、 'bottomleft' 、 'bottomcenter' 、 'bottomright'，`本参数可以覆盖全局设置`。 |
| displayMode | string | slide | [可选] 提示框显示动画(无动画、渐显渐隐、滑动)，参数['none' 、 'fade' 、 'slide']，`本参数可以覆盖全局设置`。 |
| autoClose | boolean | null | [可选] 是否自动关闭提示框，默认在type为['ok' 、 'correct' 、 'info']三种方式时参数值为true。 |
| alertTimeout | int | null | [可选] 自动关闭提示框的时间(毫秒)，autoClose参数为true时生效，`本参数可以覆盖全局设置`。 |
|mask | boolean | null | [可选] 是否模态显示提示框，默认在type为['warn'  、 'error'  、 'confirm']三种方式时参数值为true。 |
| title | string | 见bjui-regional.zh-CN.js中alertmsg | [可选] 信息提示框的标题，设置本参数将会覆盖bjui-regional.zh-CN.js中alertmsg的对应设置。 |
| okName | string | 确定 | [可选] 确定按钮的名称，设置本参数将会覆盖bjui-regional.zh-CN.js中alertmsg的对应设置。 |
| cancelName | string | 取消 | [可选] `仅type为'confirm'时有效`取消按钮的名称，设置本参数将会覆盖bjui-regional.zh-CN.js中alertmsg的对应设置。 |
| okCall | function() | null | [可选] 确定按钮的回调方法，支持字符串类型的方法名，`该方法会在提示框关闭后被调用`。 |
| cancelCall | function() | null | [可选] `仅type为'confirm'时有效`取消按钮的回调方法，支持字符串类型的方法名，`该方法会在提示框关闭后被调用`。 |

### Ajax提交表单
***
本节主要介绍框架的普通表单提交及相关参数。
#### 初始化
* Data属性：form添加属性`data-toggle="validate"`或`data-toggle="ajaxform"`。其中`data-toggle="validate"`属性需要通过验证后才能提交。

  *DOM示例代码：*
```html
<form action="ajaxDone1.html" data-toggle="validate">
    <p><label class="x85">登录名：</label><input type="text" name="username" data-rule="required" placeholder="登录名"></p>
    <p><label class="x85">密码：</label><input type="password" name="password" data-rule="required;" placeholder="登录密码"></p>
    <p class="text-center"><button type="submit" class="btn-default">提 交</button></p>
</form>
</pre>
<pre class="brush: html">
<form action="ajaxDone1.html" data-toggle="ajaxform">
    <p><label class="x85">登录名：</label><input type="text" name="username" data-rule="required" placeholder="登录名"></p>
    <p><label class="x85">密码：</label><input type="password" name="password" data-rule="required;" placeholder="登录密码"></p>
    <p class="text-center"><button type="submit" class="btn-default">提 交</button></p>
</form>
```
* jQuery API：`API方式目前不支持验证提交。`
```js
$(form).bjuiajax('ajaxForm', options)
```

#### 参数（options）

| 名称 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| confirmMsg | string | null | [可选] 提交表单前的确认提示。 |
| callback | function(json) | null | [可选] 默认由内置回调函数处理，参数json由服务端返回。 |
| loadingmask | boolean | true | [可选] ajax请求时是否显示数据加载遮罩。 |
| reload | boolean | true | `[默认回调函数使用]` 表单提交成功后，是否刷新当前窗口。 |
| reloadNavtab | boolean | false | `[默认回调函数使用](仅限dialog及局部刷新)` 表单提交成功后，是否刷新当前navtab。 |
**注意：**form如果有属性`enctype="multipart/form-data"`，支持HTML5的浏览器以FormData方式提交数据，不支持的（IE8-9）则由iframe提交。


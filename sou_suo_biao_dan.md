### Ajax搜索表单
***
本节主要介绍框架的搜索表单提交及相关参数。
#### 初始化
* Data属性：form添加属性`data-toggle="ajaxsearch"`。

  *DOM示例代码：*
```html
<form action="ajaxDone1.html" data-toggle="ajaxsearch">
    <p><label class="x85">用户名：</label><input type="text" name="username" placeholder="用户名"></p>
    <p><label class="x85">注册时间：</label><input type="text" name="date" data-toggle="datepicker" placeholder="注册时间"></p>
    <p class="text-center"><button type="submit" class="btn-default">搜索</button></p>
</form>
```
搜索表单内的按钮或a链接添加属性`data-toggle="reloadsearch"`可触发表单重载（主要用于清空查询）：
```html
<a href="javascript:;" data-toggle="reloadsearch" data-clear-query="true">清空查询</a>
```
* jQuery API：
```javascript
$(form).bjuiajax('doSearch', options)
```

#### 参数（options）

| 名称 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| url | string | null | [必选]*`D-Url`* 处理搜索的URL，如未明确指定，将自动获取form的action属性。 |
| clearQuery | boolean | false | [可选] 清除查询条件。请在`清空查询`时设为true。 |
| loadingmask | boolean | true | [可选] ajax请求时是否显示数据加载遮罩。 |


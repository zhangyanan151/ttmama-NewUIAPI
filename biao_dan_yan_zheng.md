### 第三方插件：表单验证
***
本节主要介绍表单验证插件 - nice Validaor，插件官网：[http://niceue.com/validator/](http://niceue.com/validator/)。
### 初始化
* Data属性：form添加属性`data-toggle="validate"`，form内的相关input添加验证规则(`data-rule`)后，提交表单即可触发验证。

  `注意：仅input添加验证规则，form未添加data-toggle="validate"时，提交表单仍会验证，但验证通过后不会以ajax方式提交表单。`
**`DOM示例代码：`**
```html
<form action="ajaxDone1.html" data-toggle="validate">
    <p><label class="x85">用户身份：</label><select name="role" data-rule="required" data-toggle="selectpicker">
            <option value=""></option>
            <option value="a">管理员</option>
            <option value="b">项目负责人</option>
            <option value="c">执行人</option>
        </select>
    </p>
    <p><label class="x85">登录名：</label><input type="text" name="username" data-rule="required" data-tip="你好啊，请填写用户名" data-ok="用户名可用" placeholder="登录名"></p>
    <p><label class="x85">密码：</label><input type="password" name="password" data-rule="required;" placeholder="登录密码"></p>
    <p><label class="x85">记住：</label><input type="checkbox" name="remember" value="true" id="doc-validate-remember" data-toggle="icheck" data-rule="checked" data-label="记住登陆信息"></p>
    <p><hr></p>
    <p><label class="x85"></label><button type="submit" class="btn-default">提 交</button></p>
</form>
```
* jQuery API：无

  **注意：**默认表单未通过验证时会弹出alertmsg错误字段数提示，若要取消alertmsg请在form中添加属性`data-alertmsg="false"`
  
#### 字段验证DOM参数
* 以下参数仅限于DOM传参，js传参请到插件官网查看。
* 不在form中的字段不会验证。
        </blockquote>


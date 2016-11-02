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

| 名称 | 类型 | 描述 | 示例 |
| -- | -- | -- | -- |
| data-rule | string | [必选] 定义该字段的规则集 | data-rule="required; password" |
| data-rule-\* | string | [可选] 定义临时规则 | data-rule-password="[/^\d{6}$/, '请填写6位数字']" |
| data-msg-\* | string | [可选] 更改了默认规则的消息 | data-msg-required="请填写密码" |
| data-tip | string | [可选] 当元素获得焦点时，显示友好信息 | data-tip="请输入用户名" |
| data-ok | string | [可选] 字段验证成功后显示的消息 | data-ok="用户名可用" |
| data-target | selector | [可选] 如果定义，将决定消息最终显示位置，如果selector是字段，则消息显示在字段的消息位置，否则显示在selector指定容器内。 | data-target="#username" |
| novalidate | null | [可选] 无值参数，指定该字段不需要验证。 ||
| notimely | boolean | [可选] 值为true时，指定该字段不需要适时验证 `插件官网说是无值参数，经过测试不设为true则无效`。 | notimely="true" |
#### 验证规则
**如何验证：**为字段添加属性`data-rule="规则"`即可，多条规则以`;`分隔。

`更多规则：`请查看插件官网：[http://niceue.com/validator/demo/](http://niceue.com/validator/demo/) 或查看代码文件： `/BJUI/js/bjui-regional.zh-CN.js`

| 规则 | 描述  | 示例代码 |
| -- | -- | -- |
| required | 必填项| <code><input type="text" name="doc-validate1" data-rule="required"></code> |
| 显示替换名:required | 显示替换名 + 必填项提示消息 | <code><input type="text" name="doc-validate2" data-rule="用户名:required;"></code> |
                </tr>
                <tr>
                    | match[name] |
                    | 两个字段匹配 |
                    | <input type="text" name="doc-validate-p1" size="5" data-rule="密码:required"><input type="text" name="doc-validate-p2" size="5" data-rule="确认密码:required;match(doc-validate-p1)"> |
                    | <pre class="brush:html">
                        <input type="text" name="doc-validate-p1" size="5" data-rule="密码:required">
                        <input type="text" name="doc-validate-p2" size="5" data-rule="确认密码:required;match(doc-validate-p1)">
                    </pre> |
                </tr>
                <tr>
                    | digits |
                    | 整数 |
                    | <input type="text" name="doc-validate-d1" size="10" data-rule="digits"> |
                    | <pre class="brush:html"><input type="text" name="doc-validate-d1" size="10" data-rule="digits"></pre> |
                </tr>
                <tr>
                    | number |
                    | 数字 |
                    | <input type="text" name="doc-validate-d2" size="10" data-rule="number"> |
                    | <pre class="brush:html"><input type="text" name="doc-validate-d2" size="10" data-rule="number"></pre> |
                </tr>
                <tr>
                    | mobile |
                    | 手机号 |
                    | <input type="text" name="doc-validate-m1" size="10" data-rule="mobile"> |
                    | <pre class="brush:html"><input type="text" name="doc-validate-m1" size="10" data-rule="mobile"></pre> |
                </tr>
                <tr>
                    | email |
                    | 邮箱 |
                    | <input type="text" name="doc-validate-m2" size="10" data-rule="email"> |
                    | <pre class="brush:html"><input type="text" name="doc-validate-m2" size="10" data-rule="email"></pre> |
                </tr>
                <tr>
                    | date |
                    | 日期 |
                    | <input type="text" name="doc-validate-d3" size="10" data-rule="date"> |
                    | <pre class="brush:html"><input type="text" name="doc-validate-d3" size="10" data-rule="date"></pre> |
                </tr>
                <tr>
                    | datetime |
                    | 日期时间 |
                    | <input type="text" name="doc-validate-d4" size="10" data-rule="datetime"> |
                    | <pre class="brush:html"><input type="text" name="doc-validate-d4" size="10" data-rule="datetime"></pre> |
                </tr>
                <tr>
                    | url |
                    | 网址 |
                    | <input type="text" name="doc-validate-u" size="10" data-rule="url"> |
                    | <pre class="brush:html"><input type="text" name="doc-validate-u" size="10" data-rule="url"></pre> |
                </tr>
                <tr>
                    | ID_card |
                    | 身份证 |
                    | <input type="text" name="doc-validate-id" size="10" data-rule="ID_card"> |
                    | <pre class="brush:html"><input type="text" name="doc-validate-id" size="10" data-rule="ID_card"></pre> |
                </tr>
                <tr>
                    | checked |
                    | 复选\单选框 |
                    | <input type="checkbox" name="doc-validate-cc1" id="doc-validate-cc1" data-rule="checked" data-toggle="icheck" data-label="复选框"><input type="radio" name="doc-validate-cc2" id="doc-validate-cc2-1" data-rule="checked" data-toggle="icheck" data-label="单选框"> |
                    | <pre class="brush:html">
                        <input type="checkbox" name="doc-validate-cc1" id="doc-validate-cc1" data-rule="checked" data-toggle="icheck" data-label="复选框">
                        <input type="radio" name="doc-validate-cc2" id="doc-validate-cc2-1" data-rule="checked" data-toggle="icheck" data-label="单选框">
                    </pre> |
                </tr>
            </tbody>
        </table>
        </form>
    </div>
</div>
<div class="bjui-pageFooter">
    <ul>
        <li><button type="button" class="btn-close" data-icon="close">关闭</button></li>
    </ul>
</div>


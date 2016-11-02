### 第三方插件：Kindeditor —— html编辑器
***
本节主要介绍在线HTML编辑器 - Kindeditor，插件地址：[http://kindeditor.net/](http://kindeditor.net/)。
#### 初始化
* Data属性：textarea添加属性`data-toggle="kindeditor"`后即可触发。<br>
**`DOM示例代码：`**
```html
<textarea data-toggle="kindeditor" data-items="fontname, fontsize, |, forecolor, hilitecolor, bold, italic, underline, removeformat, |, justifyleft, justifycenter, justifyright, insertorderedlist, insertunorderedlist, |, emoticons, image, link"></textarea>
```
* jQuery API：[http://kindeditor.net/docs/index.html](http://kindeditor.net/docs/index.html)
#### 参数（options）`basePath`为kindeditor插件目录

| 名称 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| pasteType | int | 2 | [可选] 粘贴类型，0:禁止粘贴, 1:纯文本粘贴, 2:HTML粘贴。 |
| minHeight | int | 260 | [可选] 编辑器的高度。 |
| autoHeightMode | boolean | false | [可选] 编辑器是否可以自动调整高度。 |
| items | string |:[^本表底部查看]| [可选] 编辑器的工具栏显示图标，多个图标名称以`,`分隔，全部工具见：[http://kindeditor.net/docs/option.html#items](http://kindeditor.net/docs/option.html#items)。 |
| uploadJson | string | basePath + 'php/upload_json.php' | [可选] 编辑器上传文件的服务器端程序。 |
| fileManagerJson | string | basePath + 'php/file_manager_json.php' | [可选] 指定浏览远程图片的服务器端程序。 |
| allowFileManager | boolean | true | [可选] 上传时是否显示浏览远程服务器按钮。 |
| fillDescAfterUploadImage | boolean | true | [可选] 上传图片成功后，为true则转到属性页，false则直接插入图片。 |
| afterUpload | function(url) | null | [可选] 上传文件后执行的回调函数。 |
| afterSelectFile | function(url) | null | [可选] 从图片空间选择文件后执行的回调函数。 |
| confirmSelect | function(url) | null | [可选] `自定义`用于上传(fillDescAfterUploadImage=true时生效)或选择图片并插入成功后的回调函数。 |
| htmlTags | object | :[^本表底部查看] | [可选] 指定要保留的HTML标记和属性，官方版见：[http://kindeditor.net/docs/option.html#htmltags](http://kindeditor.net/docs/option.html#htmltags)。 |
[^Items默认值]:
```js
[
    'source', '|', 'undo', 'redo', '|', 'preview', 'print', 'template', 'code', 'cut', 'copy', 'paste',
    'plainpaste', 'wordpaste', '|', 'justifyleft', 'justifycenter', 'justifyright',
    'justifyfull', 'insertorderedlist', 'insertunorderedlist', 'indent', 'outdent', 'subscript',
    'superscript', 'clearhtml', 'quickformat', 'selectall', '|', 'fullscreen', '/',
    'formatblock', 'fontname', 'fontsize', '|', 'forecolor', 'hilitecolor', 'bold',
    'italic', 'underline', 'strikethrough', 'lineheight', 'removeformat', '|', 'image', 'multiimage',
    'flash', 'media', 'insertfile', 'table', 'hr', 'emoticons', 'baidumap', 'pagebreak',
    'anchor', 'link', 'unlink', '|', 'about'
]
本框架配置 items 的写法：
data-items="'source', '|', 'undo', 'redo', '|', 'preview', 'print', 'template'"
`或`
data-items="source, |, undo, redo, |, preview, print, template"
 ```
        
 [^htmlTags默认值]:
 ```js
{
    font : [],
    span : ['.color', '.background-color', '.font-size', '.font-family'],
    div : ['.margin', '.padding', '.text-align'],
    table: ['align', 'width'],
    'td,th': ['align', 'valign', 'width', 'height', 'colspan', 'rowspan'],
    a : ['href', 'target', 'name'],
    embed : ['src', 'width', 'height', 'type', 'loop', 'autostart', 'quality', '.width', '.height', 'align', 'allowscriptaccess'],
    img : ['src', 'width', 'height', 'border', 'alt', 'title', 'align', '.width', '.height', '.border'],
    'p,ol,ul,li,blockquote,h1,h2,h3,h4,h5,h6' : [
        'class', 'align', '.text-align', '.color', '.font-weight', '.font-style', '.text-decoration', '.vertical-align', '.text-indent', '.margin-left'
    ],
    pre : ['class'],
    hr : ['class', '.page-break-after'],
    'br,tbody,tr,strong,b,sub,sup,em,i,u,strike,s,del' : []

}
 ```
配置更多参数请查看Kindeditor官方文档：[http://kindeditor.net/docs/index.html](http://kindeditor.net/docs/index.html)，本框架引入Kindeditor插件入口在`bjui-plugins.js`

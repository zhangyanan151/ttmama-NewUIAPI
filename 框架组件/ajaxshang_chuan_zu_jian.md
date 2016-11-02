### 上传组件
***
本节主要介绍框架的上传组件功能。在本框架中，IE8-9使用uploadify组件上传，其余支持HTML5的浏览器使用HTML5上传，两种上传的API基本一致。
#### 初始化
* Data属性：div添加属性`data-toggle="upload"`后可触发上传组件。

  *示例代码：*
```js
function doc_upload_success(file, data) {
    var json = $.parseJSON(data)

    $(this).bjuiajax('ajaxDone', json)
    if (json[BJUI.keys.statusCode] == BJUI.statusCode.ok) {
        $('#doc_pic').val(json.filename)
        $('#doc_span_pic').html('已上传图片：<img src="'+ json.filename +'" width="100">')
    }
}
```
```html
<div style="display:inline-block; vertical-align:middle;">
    <div id="doc_pic_up" data-toggle="upload" data-uploader="doc/form/ajaxPic.html" 
        data-file-size-limit="1024000000"
        data-file-type-exts="*.jpg;*.png;*.gif;*.mpg"
        data-multi="true"
        data-on-upload-success="doc_upload_success"
        data-icon="cloud-upload"></div>
    <input type="hidden" name="doc.pic" value="" id="doc_pic">
</div>
<span id="doc_span_pic"></span>
```
* jQuery API：
      $(div).uplopd(options)
 
#### 参数（options）

| 名称 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| uploader | string | null | [**必选**] <span class="badge"><i>D-Url</i></span> 上传处理URL。 |
| formData | object | {} | [可选] 发送到服务端的额外数据。 |
| fileTypeExts | string | *.jpg;*.png | [可选] 限制上传文件类型，多个以`;`分隔。 |
| fileObjName | string | file | [可选] 服务端接收到的file域名称。 |
| buttonText | string | 选择上传文件 | [可选] 上传按钮的名称。 |
| auto | boolean | false | [可选] 是否开启自动上传。 |
| multi | boolean | false | [可选] 是否支持一次性选择多个上传文件。 |
| fileSizeLimit | int | 204800 | [可选] 上传文件大小限制，单位 KB。 |
| onUploadSuccess | function(file, data, $element) | null | [**必选**] 上传成功时的回调函数，data是服务端返回的JSON数据，$element是触发上传的jQuery对象。 |
| dragDrop | boolean | false | [可选] `HTML5专用`是否开启拖动上传，开启后，将文件拖到按钮上即可上传。 |
| previewImg | boolean | true | [可选] `HTML5专用`是否预览上传图片。 |
| previewLoadimg | string | null | [可选] `HTML5专用`载入预览图片前显示的loading图标，previewImg=true时生效。 |
| icon | string | null | [可选] `HTML5专用`上传按钮的图标。 |
#### 回调函数的JSON参数

| 名称 | 类型 | 描述 |
| -- | -- | -- |
| statusCode | int | **必选。**状态码(ok = 200, error = 300, timeout = 301)，可以在BJUI.init时配置三个参数的默认值。 |
| message | string | 可选。提示信息内容。 |
| filename | string | 可选。上传成功后的文件名称或路径。 |
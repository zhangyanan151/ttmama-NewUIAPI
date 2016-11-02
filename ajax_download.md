### 第三方插件：jquery.fileDownload —— ajax下载
***
本节主要介绍ajax下载插件 - jquery.fileDownload，插件地址：[https://github.com/johnculviner/jquery.fileDownload](https://github.com/johnculviner/jquery.fileDownload)。

本框架的表格导出、datagrid的导出(exportOption参数的type='file'时)使用了该插件。
#### 使用
        <ul>
            <li><span class="label label-default">正常下载：</span>
                <script type="text/javascript">
                function doc_filedownload1(a) {
                    $.fileDownload($(a).attr('href'), {
                        failCallback: function(responseHtml, url) {
                            if (responseHtml.trim().startsWith('{')) responseHtml = responseHtml.toObj()
                            $(a).bjuiajax('ajaxDone', responseHtml)
                        }
                    })
                }
                </script>
                <a href="Book1.xlsx" onclick="doc_filedownload1(this); return false;">点我下载一个文件</a><br>
                <p>示例代码：</p>
                <pre class="brush: js; html-script: true">
                    <script type="text/javascript"&gt;
                        function doc_filedownload1(a) {
                            $.fileDownload($(a).attr('href'), {
                                failCallback: function(responseHtml, url) {
                                    if (responseHtml.trim().startsWith('{')) responseHtml = responseHtml.toObj()
                                    $(a).bjuiajax('ajaxDone', responseHtml)
                                }
                            })
                        }
                    </script&gt;
                    <!-- url 直接指向文件地址，或返回正确的文件地址 -->
                    <a href="Book1.xlsx" onclick="doc_filedownload1(this); return false;"&gt;点我下载一个文件</a&gt;
                </pre>
            </li>
            <li><span class="label label-default">下载失败：</span>
                <a href="ajaxDoneErr.html" onclick="doc_filedownload1(this); return false;">点我下载一个文件</a><br>
                <p>示例代码：</p>
                <pre class="brush: js; html-script: true">
                    <script type="text/javascript"&gt;
                        function doc_filedownload1(a) {
                            $.fileDownload($(a).attr('href'), {
                                failCallback: function(responseHtml, url) {
                                    if (responseHtml.trim().startsWith('{')) responseHtml = responseHtml.toObj()
                                    $(a).bjuiajax('ajaxDone', responseHtml)
                                }
                            })
                        }
                    </script&gt;
                    <!-- url 返回JSON信息，处理返回信息，不下载文件 -->
                    <a href="ajaxDoneErr.html" onclick="doc_filedownload1(this); return false;"&gt;点我下载一个文件</a&gt;
                </pre>
            </li>
        </ul>
    </div>
</div>
<div class="bjui-pageFooter">
    <ul>
        <li><button type="button" class="btn-close" data-icon="close">关闭</button></li>
    </ul>
</div>


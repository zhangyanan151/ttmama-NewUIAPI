### 第三方插件：zTree —— 树插件
***
本节主要介绍jQuery树插件 - zTree，插件地址：[http://www.ztree.me/](http://www.ztree.me/)。
#### 初始化
        <ul>
            <li><span class="label label-default">DOM示例1：</span>ul添加id, 添加class`(ztree)`和属性`data-toggle="ztree"`后即可触发，data属性设置要展示的JSON数据及其他参数。<br>
                <p>示例代码：</p>
                <pre class="brush: html">
                    <ul id="ztree-test-demo1" class="ztree" data-toggle="ztree" data-nodes="[{id:1,pid:0,name:'表单元素',faicon:'rss',children:[{id:10,pId:1,name:'按钮'},{id:11,pId:1,name:'文本框'}]}]"></ul>
                </pre>
            </li>
            <li><span class="label label-default">DOM示例2：</span>ul添加id, 添加class`(ztree)`和属性`data-toggle="ztree"`后即可触发，然后使用集合属性`data-options`定义JSON数据及其他参数。<br>
                <p>示例代码：</p>
                <pre class="brush: html">
                    <ul id="ztree-test-demo2" class="ztree" data-toggle="ztree" data-options="{nodes:[{id:1,pid:0,name:'表单元素',faicon:'rss',children:[{id:10,pId:1,name:'按钮'},{id:11,pId:1,name:'文本框'}]}]}"></ul>
                </pre>
            </li>
            <li><span class="label label-default">DOM示例3：</span>ul添加id, 添加class`(ztree)`和属性`data-toggle="ztree"`后即可触发，使用li元素定义要展示的数据。<br>
                <p>示例代码：</p>
                <pre class="brush: html">
                    <ul id="ztree-test-demo3" class="ztree" data-toggle="ztree">
                        <li data-id="1" data-pid="0" data-faicon="rss" data-faicon-close="cab">表单元素</li>
                        <li data-id="10" data-pid="1" data-url="form-button.html" data-tabid="form-button" data-faicon="bell">按钮</li>
                        <li data-id="11" data-pid="1" data-url="form-input.html" data-tabid="form-input" data-faicon="info-circle">文本框</li>
                    </ul>
                </pre>
            </li>
            <li>jQuery API：<a href="http://www.ztree.me/v3/api.php" target="_blank">http://www.ztree.me/v3/api.php</a></li>
        </ul>
        <blockquote class="point">
            <p>考虑到nodes定义的JSON数据写到HTML中可能会破坏DOM结构， nodes参数支持定义为方法名，该方法返回需要的JSON数据。例：</p>
            <pre class="brush: js; html-script: true">
                <script type="text/javascript">
                    function ztree_returnjson() {
                        return [{id:1,pid:0,name:'表单元素',children:[{id:10,pId:1,name:'按钮'},{id:11,pId:1,name:'文本框'}]}]
                    }
                </script>
                <ul id="ztree-test-demo2" class="ztree" data-toggle="ztree" data-options="{nodes:'ztree_returnjson'}"></ul>
            </pre>
        </blockquote>
        <h4>DOM初始化的zTree参数</h4>
        <blockquote>
            <p>推荐使用集合属性`data-options`定义参数，如果使用`data属性`定义参数，注意转换成对应的名称，参见<a href="doc/base/data.html" data-toggle="navtab" data-id="doc-base">data属性</a>一节。</p>
        </blockquote>
        <table class="table table-striped table-hover">
            <thead>
                <tr>
                    <th width="160">属性名称</th>
                    <th>类型、参数</th>
                    <th>默认值</th>
                    <th>描述信息</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    | nodes |
                    | object/string/function |
                    | null |
                    | zTree展示的JSON数据，参数格式可以是：JSON对象，JSON格式的字符串，返回JSON数据的方法名，返回JSON数据的方法 |
                </tr>
                <tr>
                    | └ faicon |
                    | string |
                    | null |
                    | 定义zTree节点显示的字体图标，图标名称见<a href="http://fortawesome.github.io/Font-Awesome/icons/" target="_blank">Font Awesome</a>，定义图标名称不要加`fa-` |
                </tr>
                <tr>
                    | └ faiconClose |
                    | string |
                    | null |
                    | 定义zTree父节点折叠后显示的字体图标。 |
                </tr>
                <tr>
                    | expandAll |
                    | Boolean |
                    | false |
                    | 展开整棵树 |
                </tr>
                <tr>
                    | simpleData |
                    | Boolean |
                    | true |
                    | 使用简单JSON数据 |
                </tr>
                <tr>
                    | addHoverDom |
                    | function(treeId, treeNode) |
                    | null |
                    | 鼠标放到节点上时，显示的自定义DOM，函数可选字符串"edit"：显示自定义的添加和删除按钮，删除按钮点击时有确认事件，如果定义了删除事件[onRemove]，则删除时将调用该事件，否则直接删除 |
                </tr>
                <tr>
                    | removeHoverDom |
                    | function(treeId, treeNode) |
                    | null |
                    | 鼠标离开节点时，隐藏自定义DOM，函数可选字符串"edit"：隐藏自定义的添加和删除按钮，addHoverDom和removeHoverDom需要同时出现 |
                </tr>
                <tr>
                    | maxAddLevel |
                    | Int |
                    | 2 |
                    | 允许添加的最大子节点深度，仅使用默认的{"addHoverDom":"edit"}时有效，level > maxAddLevel 的节点上将不会显示添加按钮。 |
                </tr>
                <tr>
                    | addDiyDom |
                    | function(treeId, treeNode) |
                    | false |
                    | 用于在节点上固定显示用户自定义DOM |
                </tr>
                <tr>
                    | editEnable |
                    | Boolean |
                    | false |
                    | 允许编辑节点 |
                </tr>
                <tr>
                    | showRemoveBtn |
                    | Boolean |
                    | false |
                    | 显示默认的编辑按钮 |
                </tr>
                <tr>
                    | showRenameBtn |
                    | Boolean |
                    | false |
                    | 显示默认的删除按钮 |
                </tr>
                <tr>
                    | checkEnable |
                    | Boolean |
                    | false |
                    | 设置 zTree 的节点上是否显示 checkbox / radio |
                </tr>
                <tr>
                    | chkStyle |
                    | String |
                    | checkbox |
                    | 勾选框类型(checkbox 或 radio）[ {"checkEnable":true} 生效 ] |
                </tr>
                <tr>
                    | radioType |
                    | String |
                    | all |
                    | radio 的分组范围，参数'all'：整棵树为一个分组，参数'level'：每一节点范围当作一个分组 |
                </tr>
                <tr>
                    | onClick |
                    | function(event, treeId, treeNode, clickFlag) |
                    | null |
                    | 用于捕获节点被点击的事件回调函数，<br>请为该函数添加`event.preventDefault()`以阻止a链接的默认事件
                     |
                </tr>
                <tr>
                    | beforeDrag |
                    | function(treeId, treeNodes) |
                    | null |
                    | 用于捕获节点被拖拽之前的事件回调函数，并且根据返回值确定是否允许开启拖拽操作<br>
                        拖拽需要开启(editEnable)：[ {"editEnable":true} 生效 ]
                     |
                </tr>
                <tr>
                    | beforeDrop |
                    | function(treeId, treeNodes, targetNode, moveType, isCopy) |
                    | null |
                    | 用于捕获节点拖拽操作结束之前的事件回调函数，并且根据返回值确定是否允许此拖拽操作 |
                </tr>
                <tr>
                    | onDrop |
                    | function(event, treeId, treeNodes, targetNode, moveType, isCopy) |
                    | null |
                    | 用于捕获节点拖拽操作结束的事件回调函数 |
                </tr>
                <tr>
                    | beforeRemove |
                    | function(treeId, treeNode) |
                    | null |
                    | 用于捕获节点被删除之前的事件回调函数，并且根据返回值确定是否允许删除操作。 |
                </tr>
                <tr>
                    | onRemove |
                    | function(event, treeId, treeNode) |
                    | null |
                    | 用于捕获删除节点之后的事件回调函数。 |
                </tr>
                <tr>
                    | onCheck |
                    | function(event, treeId, treeNode) |
                    | null |
                    | 用于捕获 checkbox / radio 被勾选 或 取消勾选的事件回调函数 |
                </tr>
                <tr>
                    | `setting` |
                    | object |
                    | null |
                    | 用于定义更多的zTree参数，更多参数请查看zTree API：<a href="http://www.ztree.me/v3/api.php" target="_blank">http://www.ztree.me/v3/api.php</a> |
                </tr>
            </tbody>
        </table>
    </div>
</div>
<div class="bjui-pageFooter">
    <ul>
        <li><button type="button" class="btn-close" data-icon="close">关闭</button></li>
    </ul>
</div>


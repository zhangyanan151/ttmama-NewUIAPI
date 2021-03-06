### 横向导航菜单(hnav)
***
本节介绍B-JUI框架的横向导航菜单，html结构如下：
```html
<div id="bjui-hnav">
    <button type="button" class="bjui-hnav-toggle btn-default" data-toggle="collapse" data-target="#bjui-hnav-navbar">
        <i class="fa fa-bars"></i>
    </button>
    <ul id="bjui-hnav-navbar">
        <!-- 欢迎 -->
        <li style="width:204px;"><a>欢迎您，超级管理员！</a></li>

        <!-- zTree菜单 - BEGIN -->
        <li class="active"><a href="javascript:;" data-toggle="slidebar">表单元素</a>
            <div class="items hide" data-noinit="true">
                <ul id="bjui-hnav-tree-input" class="ztree ztree_main" data-toggle="ztree" data-on-click="MainMenuClick" data-expand-all="true" data-faicon="check-square-o" data-title="基本元素">
                    <li data-id="1" data-pid="0" data-faicon="folder-open-o" data-faicon-close="folder-o">表单元素</li>
                    <li data-id="10" data-pid="1" data-url="form-button.html" data-tabid="form-button" data-faicon="hand-o-up">按钮</li>
                    <li data-id="11" data-pid="1" data-url="form-input.html" data-tabid="form-input" data-faicon="terminal">文本框</li>
                    <li data-id="12" data-pid="1" data-url="form-select.html" data-tabid="form-select" data-faicon="caret-square-o-down">下拉选择框</li>
                    <li data-id="13" data-pid="1" data-url="form-checkbox.html" data-tabid="table" data-faicon="check-square-o">复选、单选框</li>

                </ul>
                <ul id="bjui-hnav-tree-form" class="ztree ztree_main" data-toggle="ztree" data-on-click="MainMenuClick" data-expand-all="true" data-faicon="list" data-title="综合演示">
                    <li data-id="1" data-pid="0" data-faicon="folder-open-o" data-faicon-close="folder-o">表单演示</li>
                    <li data-id="14" data-pid="1" data-url="form.html" data-tabid="form" data-faicon="list">表单综合演示</li>
                </ul>
            </div>
        </li><!-- zTree菜单 - END -->

        <!-- 列表菜单 - BEGIN -->
        <li><a href="javascript:;" data-toggle="slidebar">表单元素&演示</a>
            <div class="items hide" data-noinit="true">
                <ul class="menu-items" data-faicon="hand-o-up">
                    <li><a href="form-button.html" data-options="{id:'form-button', faicon:'hand-o-up'}">按钮</a><b><i class="fa fa-angle-down"></i></b>
                        <!-- 子级菜单 -->
                        <ul class="menu-items-children">
                            <li><a href="form-input.html" data-options="{id:'form-input', faicon:'terminal'}">文本框</a></li>
                            <li><a href="form-select.html" data-options="{id:'form-select', faicon:'caret-square-o-down'}">下拉选择框</a></li>
                        </ul>
                    </li>
                    <li><a href="form-input.html" data-options="{id:'form-input', faicon:'terminal'}">文本框</a></li>
                    <li><a href="form-select.html" data-options="{id:'form-select', faicon:'caret-square-o-down'}">下拉选择框</a></li>
                    <li><a href="form-checkbox.html" data-options="{id:'form-checkbox', faicon:'check-square-o'}">复选、单选框</a></li>
                </ul>
                <ul class="menu-items" data-title="表单Demo" data-faicon="list">
                    <li><a href="form.html" data-options="{id:'form-demo', faicon:'th-large'}">表单示例</a></li>
                </ul>
            </div>
        </li><!-- zTree菜单 - End -->

        <!-- 下拉菜单 - BEGIN -->
        <li><a href="#" class="dropdown-toggle" data-toggle="dropdown"><!-- 下拉菜单 --></a>
            <ul class="dropdown-menu" role="menu">
                <li><a href="#"><!-- 下拉菜单一 --></a></li>
                <li><a href="#"><!-- 下拉菜单二 --></a></li>
                ...
            </ul>
        </li><!-- 下拉菜单 - END -->
        ...
    </ul>
</div>
```
  **说明** 
  * 横向菜单(#bjui-hnav-navbar)的li元素添加Class`active`，并含有class为`items hide`包裹有zTree菜单或列表菜单的div，则在框架初始化完成后，对应的zTree或列表会自动加载到左侧导航栏
  * zTree菜单：横向菜单的a链接属性 `data-toggle`为`slidebar`时，点击本链接将对应的zTree或列表加载到左侧导航栏
  * 下拉菜单：横向菜单的a链接属性 `data-toggle`为`dropdown`时，触发下拉菜单
  * div(items)容器中的ul属性`data-faicon`可以定义左侧导航栏模块的icon图标，属性`data-tit`可定义模块的名称


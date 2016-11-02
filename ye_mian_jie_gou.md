### 页面结构
***
* B-JUI仅有一个主页面(document)，框架内的所有子页面将通过Ajax获取后作为一个页面片段附加到主页面上，外部页面则通过iframe嵌入主页面， 本节介绍 B-JUI的主页面结构。

#### HTML5 文档类型
* 同Bootstrap， B-JUI使用 HTML5 文档类型，参照下面的格式进行设置。
`

      <DOCTYPE html>
      <html lang="zh-CN">
      ...
      </html>


#### 主页面结构(仅body部分)
* 主页面由上（页头）、中左（导航菜单）、中右（工作区）、下（页脚）四部分组成，其中左侧导航菜单可收缩。结构如下：
      <header id="bjui-header">
            <!-- logo --><!-- 快捷菜单(消息、用户信息、切换皮肤) -->
            <div id="bjui-hnav">
                <!-- 横向菜单 -->
            </div>
       </header>
       <div id="bjui-container" class="clearfix">
            <div id="bjui-leftside">
                <!-- 导航栏 -->
            </div>
            <div id="bjui-navtab" class="tabsPage">
                <!-- 工作区(navtab) -->
           </div>
       </div>
       <footer id="bjui-footer">
            <!-- 页脚 -->
       </footer>
        
#### 子页面（即页面片段[后面简称：页片]）标准结构
* 页片通常由三部分组成，也可以只保留bjui-pageContent部分，或者自定义内容。一个标准的页片结构如下：
        <div class="bjui-pageHeader">
            <!-- 顶部模块[如：功能按钮、搜索面板] -->
        </div>
        <div class="bjui-pageContent">
            <!-- 内容区 -->
        </div>
        <div class="bjui-pageFooter">
            <!-- 底部模块[如：工具条、分页组件]  -->
        </div>
        
** 注意1： **在标准结构中，`bjui-pageHeader`和 `bjui-pageFooter`部分是固定在页片中的，```bjui-pageContent```中的内容溢出会出现滚动条。

** 注意2： ** `bjui-pageContent` 默认padding 10px，像表格之类的布局不需要padding的，需要再添加个Class: `tableContent`



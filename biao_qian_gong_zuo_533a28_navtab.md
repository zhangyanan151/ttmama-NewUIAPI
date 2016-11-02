### 标签工作区(navtab)
***
* B-JUI框架的整个工作区部分就是一个navtab组件，本组件位于主页面的"`#bjui-container`"容器内，固定的html结构如下：
      <div id="bjui-navtab" class="tabsPage">
          <div class="tabsPageHeader">
              <div class="tabsPageHeaderContent">
                  <ul class="navtab-tab nav nav-tabs">
                      <li><a href="javascript:;"><span>我的主页</span></a></li>
                  </ul>
              </div>
              <div class="tabsLeft"><i class="fa fa-angle-double-left"></i></div>
              <div class="tabsRight"><i class="fa fa-angle-double-right"></i></div>
              <div class="tabsMore"><i class="fa fa-angle-double-down"></i></div>
          </div>
          <ul class="tabsMoreList">
              <li><a href="javascript:;">我的主页</a></li>
          </ul>
          <div class="navtab-panel tabsPageContent">
              <div class="page unitBox">
                  <!-- 主页内容 -->
              </div>
              <!-- 各页片内容区域 -->
          </div>
      </div>
      
      
**注意：**可为主页指定载入的页面url及自动刷新等参数，如：

        <li><a href="javascript:;" data-url="index_layout.html" data-autorefresh="true"><span>我的主页</span></a></li>


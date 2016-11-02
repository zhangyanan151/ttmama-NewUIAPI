### <ECharts图表说明
***
本节主要介绍框架的ECharts图形报表功能（由 [小策一喋](http://www.topjui.com) 整合图表库ECharts），Demo演示只展示了3种常用的图形报表：饼图、柱状/拆线图及地图，其它图表类型请根据ECharts图表库使用方法生成对应的json数据格式即可，更多图表类型及参数请查看[ECharts官网](http://echarts.baidu.com)

**`界面调用：`**在HTML代码中加入代码
```html
<div style="mini-width:400px;height:350px" data-toggle="echarts" data-type="pie,funnel" data-theme="blue" data-url="echarts-barData.html"></div>
```
**`图表数据：`**图表的JSON数据通过AJAX调用，data-url参数值为图表JSON数据调用地址，Demo演示中的图表JSON数据请进入对应的html文件查看
#### 参数（options）
        <table class="table table-bordered table-striped table-hover">
            <thead>
                <tr>
                    <th>名称</th>
                    <th>类型</th>
                    <th>默认值</th>
                    <th>描述</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    | url |
                    | string |
                    | null |
                    | [必选] 图表JSON数据调用地址 |
                </tr>
                <tr>
                    | type |
                    | string |
                    | null |
                    | [必选] 图表类型，按需加载，如需两种图表类型切换，请用 ',' 隔开</br>可选类型：bar,chord,eventRiver,force,funnel,gauge,k,line,map,pie,radar,scatter，具体类型所对应的图形请查看<a href="http://echarts.baidu.com" target="_blank">ECharts官网</a> |
                </tr>
                <tr>
                    | theme |
                    | string |
                    | default |
                    | [可选] 图表主题，按需加载，可选主题：blue,dark,default,gray,green,helianthus,infographic,macarons,red,shine，具体颜色效果请查看<a href="http://echarts.baidu.com" target="_blank">ECharts官网</a> |
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


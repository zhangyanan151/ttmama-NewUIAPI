### Highcharts图表说明
***
本节主要介绍框架的Highcharts图形报表功能（由 [小策一喋](http://www.topjui.com)</a> 整合图表库Highcharts），Demo演示只展示了3种常用的图形报表：3D饼图、折线图及3D柱状图，其它图表类型请根据Hightcharts图表库使用方法生成对应的json数据格式即可，更多图表类型及参数请查看[Highcharts中文网](http://www.hcharts.cn)

**`界面调用：`**在HTML代码中加入代码
```html
<div style="min-width:400px;height:350px" data-toggle="highcharts" data-url="chart-lineData.html"></div>
```
**`图表数据：`**图表的JSON数据通过AJAX调用，data-url参数值为图表JSON数据调用地址，Demo演示中的图表JSON数据请进入对应的html文件查看<br>
**`图表主题：`**设置图表主题，在index.html中引入BJUI/plugins/highcharts/themes下对应的js主题文件即可，例如：
```js
<script src="BJUI/plugins/highcharts/themes/dark-unica.js"></script>
```
#### 参数（options）

| 名称 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| url | string | null | [必选] 图表JSON数据调用地址 |
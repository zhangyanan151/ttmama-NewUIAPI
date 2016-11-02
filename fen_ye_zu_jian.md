### 分页组件
***
本节主要介绍框架的分页组件。
> 处理方式及参数位置参见前一节：`字段排序`。
> 
  分页组件通常放置在页脚中`div[class="bjui-footBar"]`。
>  
  分页组件不包含调整页大小参数，如需要调整页大小，需要如下代码：
  ```html
<div class="pages">
  <span>每页&nbsp;</span>
    <div class="selectPagesize">
      <select data-toggle="selectpicker" data-toggle-change="changepagesize">
          <option value="5">5</option>
          <option value="30">30</option>
          <option value="60">60</option>
          <option value="100">100</option>
      </select>
    </div>
  <span>&nbsp;条，共 10 条</span>
</div>
  ```
  
#### 初始化
* Data属性：div添加属性`data-toggle="pagination"`，添加`Class[ pagination-box ]`。
*DOM示例代码*：`分页组件默认右浮动，若要左浮动需添加Class[ pull-left ]`
```html
<div class="pagination-box" data-toggle="pagination" data-total="10" data-page-size="5" data-page-current="1"></div>
```
* jQuery API：
            $(div).pagination(options)
#### 参数（options）

| 名称 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| total | int | 0 | [必选] 总记录数。 |
| pageSize | int | 10 | [可选] 页大小(每页记录数)。 |
| pageCurrent | int | 1 | [可选] 当前页。 |
| pageNum | int | 10 | [可选] 显示的数字页码个数。 |


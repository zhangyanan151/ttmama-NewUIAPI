### 表格字段排序
***
本节主要介绍表格的字段排序，支持普通表格和固定表头表格。
> 本框架的字段排序和分页都`不是客户端处理`，是通过将参数提交到服务端，处理好后再返回页面呈现。
> 
> `提交到服务端的参数位置：`排序字段（字段名和排序方向）及 分页参数（当前页和页大小）都通过页片中的`#pagerForm`提交。
>
>  `#pagerForm`需要内置4个隐藏的input存放上述参数，代码如下：
  ```html
  <input type="hidden" name="pageSize" value="${model.pageSize}">             <!-- 页大小 -->
  <input type="hidden" name="pageCurrent" value="${model.pageCurrent}">       <!-- 当前页 -->
  <input type="hidden" name="orderField" value="${param.orderField}">         <!-- 排序字段 -->
  <input type="hidden" name="orderDirection" value="${param.orderDirection}"> <!-- 排序方向 -->
  ```
  `注意1：`如果页片中`没有#pageForm`，`将不能触发`字段排序及分页，如果`#pageForm没有放置参数input`，框架会`自动加入`。
  `注意2：`如果修改了框架初始化参数`pageInfo`，请注意手动放置的参数input的name要与之一致，如果不一致框架将会自动加入`pageInfo`定义的参数input。
  
#### 初始化
* Data属性：th元素添加属性`data-order-field="排序字段名"`后，th会自动添加排序按钮，点击按钮即可触发排序操作。
*DOM示例示例代码*(仅表头部分)：
```html
<thead>
    <tr>
        <th data-order-field="operation">ID</th>
        <th data-order-field="name">姓名</th>
        <th data-order-field="sex">性别</th>
        <th data-order-field="birthday">出生日期</th>
        <th data-order-field="birthplace">出生地</th>
    </tr>
</thead>
```
* jQuery API：
```js
$(th).tablefixed('setOrder', options)
```

#### 参数（options）

| 名称 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| orderField | string | null | [必选] 发送到服务端的排序字段名称。 |
| orderDirection | string | null | [可选值( asc/desc )] `非发送到服务端的参数`仅用于标示当前字段的排序方向。 |



### 右键菜单
***
本节主要介绍框架的自定义右键菜单。
#### 初始化
* jQuery API：`右键菜单仅支持jQuery API初始化`
```js
$(selector).contextmenu('show', options)
```
*示例代码：*
```html
<button type="button" class="btn-blue" id="doc-contextmenu-example">请用鼠标右键点我</button>
```
```js
$('#doc-contextmenu-example').contextmenu('show', 
  {
      items:[
         {
             icon  : 'plus',
             title : '新增菜单',
             func  : function(parent, menu) {
                 console.log(parent)
                 console.log('第一个菜单 -- 新增！')
             }
         },
         {
             icon  : 'apple',
             title : '苹果菜单',
             func  : function(parent, menu) {
                 console.log(menu)
                 console.log('第二个菜单 -- 苹果菜单！')
             }
         },
         {
             title : 'diver'
         },
         {
             title : '无执行方法的菜单'
         },
         {
             title : '其他菜单',
             func  : function(parent, menu) {
                 console.log('其他菜单！')
             }
         }
     ]
  }
)
```

#### 参数（options）

| 名称 | 类型 | 默认值 | 描述 |
| -- | -- | -- | -- |
| items | array[object(title, func)] | null | [必选] 右键菜单名称及对应方法的数组，object的参数见下面两行。 |
| └ items - icon | string | null | [可选] 右键菜单的图标([Font Awesome](http://fortawesome.github.io/Font-Awesome/icons/))，`用法同button的图标`。 |
| └ items - title | string | null | [必选] 右键菜单的名称，`当title="diver"时，将生成一条分隔线`。 |
| └ items - func | function(parent, menu) | null | [可选] 点击右键菜单时执行的方法，parent = 弹出右键菜单的jQuery对象，menu = 被点击菜单的jQuery对象。 |
| exclude | selector | null | [可选] 不触发右键菜单的子元素的jQuery选择器。 |
| shadow | boolean | true | [可选] 是否显示右键菜单的阴影效果。 |

### data属性
***
本框架内置组件及部分插件都可以通过data属性来初始化并使用，通常通过data-toggle来调用API。如无特殊说明，相关参数也通过data属性传递。

* data属性无法向JS传递含有大写字母的参数，如果参数是驼峰格式(大小写混搭)，则需将大写字母转换为`-`加小写。如：
  `reloadWarn` --> `data-reload-warn`
  
  `maxAddLevel` --> `data-max-add-level`
  
* 以下是data属性应用示例（打开一个navtab标签）：
      <a href="form.html" data-toggle="navtab" data-id="navtab-form" data-title="表单应用">打开一个表单应用的navtab</a>
        </pre>
* 点击上面的a链接后，将打开一个名为“表单应用”的navtab，其效果等同下面的js：
      $(selector).navtab({id:'navtab-form', url:'form.html', title:'表单应用'})
* `selector`是符合jQuery规范的选择器。

  1. 为了方便使用，如无特殊说明，`selector`可以是任意元素的选择器(不确定或在直接定义的function中，使用`$(this)`>即可)，
  2. 如开始创建了navtab：`$('.openTab').navtab({id:'myid', url:'myurl', title:'mytitle'})`，
  3. 然后又刷新该navtab：`$('.refreshTab').navtab('refresh', 'myid')`，
  4. 虽然两次触发操作同一navtab的`selector`并不一致，但并不影响使用。
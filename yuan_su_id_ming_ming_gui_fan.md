### 元素ID命名规范
***
因为本框架默认所有内容都位于一个Document中，所以为元素命名ID的时候需要做到唯一性，如果确实不可避免的会出现有重复ID的现象，需要操作当前页片的元素时，尽量用：

  `$.CurrentNavtab.find('#dom-id')`，在当前标签工作区中查找指定ID的元素。
  
  或 `$.CurrentDialog.find('#dom-id')`，在当前弹窗中查找指定ID的元素。


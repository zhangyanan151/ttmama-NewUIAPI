### URL动态赋值
本节主要介绍框架内URL的动态赋值。

`示例：`
* URL动态赋值：指的是url中包含`{ selector }`，即花括号括起来的jQuery选择器，当提交该url时，框架会自动将`selector对应元素的值` 替换到 `花括号所占区域`。

**注意：**后面的文档中，凡是标记有 * `D-Url` * 字样的URL参数，均支持动态赋值，通常支持动态赋值的url，同时支持`warn参数`，warn参数携带动态赋值不成功时的提示信息。

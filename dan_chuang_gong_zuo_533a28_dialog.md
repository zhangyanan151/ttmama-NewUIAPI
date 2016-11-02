### 弹窗工作区(dialog)
***
弹出窗口分为普通弹出窗口和模态弹出窗口，普通弹出窗口可通过taskBar组件进行最小化等操作。弹出窗口的DOM结构会放入主页面的`body`中，结构如下：
```html
<div class="bjui-dialog bjui-dialog-container">
    <div class="dialogHeader">
        <!-- 最大化、最小化、关闭等按钮区 -->
        <h1><!-- 标题 --></h1>
    </div>
    <div class="dialogContent unitBox">
        <!-- 页片内容区 -->
    </div>
    <!-- 用于调整大小的div片断 -->
</div>
```
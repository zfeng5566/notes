### JavaScript

#### <script\>`async`和`defer`属性和区别
![async与defer的区别](../images/script_defer_async.png)

**警告：**

> 多个`async`属性或`defer`脚本在现实当中，并不一定会按照顺序执行。因此确保两者之间互不依赖非常重要。
> `defer`属性脚本在现实当中，不一定会在`DOMContentLoaded`事件触发前执行，因此最好只包含一个延迟脚本。

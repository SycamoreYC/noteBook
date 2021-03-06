# 02 在HTML中使用Js

需要解决的重要问题：

如何做到让Js既能与HTML页面共存，又不影响那些页面在其他浏览器中呈现的效果。

解决方法：

为Web增加统一的脚本支持。

## 2.1 <script>标签 

​	使用<script>元素是向HTML页面中插入Js的主要方法。

​	使用<script>元素的方式有两种：

- 直接在页面中嵌入Js代码；
- 包涵外部Js文件。

需要添加src属性，指向外部Js文件的链接。

src属性还可以包含来自外部域的Js文件。

只要不存在defer和async属性，浏览器都会按照<script>元素在也页面中出现的先后顺序对它们依次进行解析。

### 2.1.1 标签的位置

​	所有<script>元素都应该放在页面的<head>元素中。

这样做的缺点：如果应用需要大量Js代码，网页打开速度会很慢。

原因：页面内容会等全部的Js代码都被下载、解析和执行完成以后，才能开始呈现页面的内容。

解决方法：将全部Js引用放在<body>元素中页面的内容后面。这样在解析包含的Js代码之前，页面的内容将完全呈现在浏览器中。

### 2.1.2 延迟脚本

​	<script>元素的的defer属性：表明脚本在执行时不会影响页面的构造。也就是说，脚本会被延迟到整个页面都解析完毕后再运行。延迟脚本不一定会按照顺序执行，也不一定会在DOMContentLoaded事件触发前执行，因此最好只包含一个延迟脚本。

defer属性只适用于外部脚本文件。

有的浏览器会忽略这个属性，像平常一样处理脚本。因此把延迟脚本放在页面底部仍然是最佳选择。

### 2.1.3 异步脚本

​	<script>元素的async属性：

与defer属性相似，都用于改变处理脚本的行为，同样只适用于外部脚本文件，并告诉浏览器立即下载文件。

不同的是：标记为async的脚本并不保证按照指定它们的先后顺序执行。因此，确定两个脚本文件互不依赖非常重要。

目的：不让页面等待两个脚本下载和执行，从而异步加载页面其它内容。故建议：异步脚本不要在加载期间修改DOM。








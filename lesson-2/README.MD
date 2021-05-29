### <script> 元素

1.  async 立即开始下载脚本
2.  charset 可选
3.  crossorigin可选 
4. defer
5.  integrity
6. type可选
### src 属性是一个完整的URL,会像路径发送一个GET请求,


#### 标签位置 
body里面的最下面 用户感觉页面加载更快了

#### 推迟执行脚本 defer
1. 脚本执行的时候不会改变页面的结构
2. 不用域名、保持顺序
3. 在DOMContentLoaded事件之前执行
4. 对于XHTML文档  defer="defer"

#### 异步脚本执行脚本 async
1. 没有顺序 立即执行
2. 在也没的load之前执行,可能会在DOMContentLoaded(17章节)
####  动态添加脚本
1. 相当于 async
2. 预加载器知道这些动态请求文件的存在 <link rel="preload" href="https://cdn.jsdelivr.net/npm/vue">

#### XHTML(可扩展性超文本标记语言)
1. 是HTML作为XML 重新包装的包装的结果
2. type="text/javascript"
3. < 替换成 
```
  &lt;
```
4. 可以包含任意文本的区块
```
<![CDATA[]]>
```

## 行内代码与外部代码


### 推荐外部文件的理由

1. 可维护性(一个文件更容易维护)
2. 缓存(两个页面都需要同一个文件,只需下载一次)(特定的设置缓存)
3. 适应未来
4. 浏览器如果支持SPDY/HTTP2 ,可以缓存


## 文档模式
1. 使用doctype切换文档模式(混杂模式和标准模式)
2. 区别在 css选荣内容方面
3. 准标准模式(图片元素周围的空白)

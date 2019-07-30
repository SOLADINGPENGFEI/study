---
sidebar: auto
sidebarDepth: 2
---
# 项目优化

## 为什么需要项目优化
在互联网快速发展的今天，在实现完功能之后，项目优化是一个被经常提到的话题。很多项目会在开发排期中留大量时间去做一轮又一轮的性能优化，就是为了让页面尽可能早的到达用户，提高交互的流畅程度。   

在系统可利用系统资源有限的大背景下，3秒呈现内容的原则下，项目优化显得格外重要。  

每减少0.1秒加载速度可能会给你带来几百甚至几千的用户活跃；每减少100K的内容请求可能会给你带来几千甚至几万的的服务端费用；每提高10%的交互流畅度可能给你带来几万甚至几十万的销售额。  

于情于理，我们都需要去了解，掌握和使用网站优化这项必备技能。 

## 雅虎的网站优化准则
由之前的十四条增加到三十五条，划分为七个模块：Content,Server,Cookie,Css,Javascript,Images,Mobile
- 国内还可以找到十四条的译文 [传送门](https://blog.csdn.net/u010648555/article/details/50721751)
- 英文版原文，小白慎入，高手必读 [传送门](https://developer.yahoo.com/performance/rules.html?guccounter=1&guce_referrer=aHR0cHM6Ly9ibG9nLmNzZG4ubmV0L3UwMTA2NDg1NTUvYXJ0aWNsZS9kZXRhaWxzLzUwNzIxNzUx&guce_referrer_sig=AQAAAAYBcLTrFIOSAc2nz_tJ2jJMy3D61wk60ga-6KZXsRrj83AeYOmAPAtidujFN2XiU96F4Fzg8aApC5q7jQeB3gybDbzDxEtVdXcQr3vzjRGb_AgvB94xZy-mGs3QKuYFe5HxvaqSV01uVqvi4SZmRCmCPDIu0K0TnYwMF9AY5n6W)


## 常见优化方法
从资源请求数量+代码执行效率两个角度来考虑
- DOM结构
    - 样式表放在头部，防止白屏和闪屏
    - JS脚本放在底部或异步获取，防止阻塞资源加载
    - 使用语义化标签，优化精简DOM结构
    - 减少DOM操作频率
    - 减少重绘与回流
- JS脚本
    - 优化脚本结构，移除重复的脚本
    - 模块就近加载（CMD）
    - 按需加载加载组件和路由
    - 图片懒加载，列表分页
    - 使用节流与防抖减少事件触发频率
    - 尽量使用CSS动画代替js动画，开启硬件加速
- 资源打包上线
    - 使用打包构建工具（webpack）清除注释，压缩页面资源，js、css、html、图片、字体等等
    - 混淆js代码
    - 分离非业务逻辑相关vendor依赖，使用长缓存缓存和CDN分发网络
- 服务器优化
    - 减少Http请求，合并页面资源，js，css单一入口。js特殊可以分为两个文件，一个业务逻辑，一个非业务逻辑
    - 把小图标合成雪碧图，不太适用经常更新的移动端开发
    - 把小的图片，字体等资源base64化
    - 开启GZip压缩，减少资源传输大小
    - [使用强缓存和协商缓存，减少资源重复请求](https://soladingpengfei.github.io/study/zh/standard/Cache.html)
- SEO优化技巧
    meta标签的作用有：搜索引擎优化（SEO），定义页面使用语言，自动刷新并指向新的页面，实现网页转换时的动态效果，控制页面缓冲，网页定级评价，控制网页显示的窗口等！
- 其他SEO优化技巧
   - 简化代码结构，更利于搜索引擎分析抓取有用内容，所有js、css采用外联方式，图片采用css精灵，减少请求次数。

   - 利用布局，把重要内容HTML代码放在最前。搜索引擎抓取HTML内容是从上到下，利用这一特点，可以让主要代码优先读取，广告等不重要代码放在下边。例如，在左栏和右栏的代码不变的情况下，只需改一下样式，利用float:left;和float:right;就可以随意让两栏在展现上位置互换，这样就可以保证重要代码在最前，让爬虫最先抓取。同样也适用于多栏的情况。

   - 每个页面只能出现一次H1标签，H2标签可以多次：H1权重很高，普遍认为仅次于title，一般资讯详情页的标题、商品详情页的标题，都放在H1里。

   - 图片一定要添加alt属性，title属性可选：蜘蛛不认识图片上的内容，只能通过alt属性来判断，如果是商品列表页，所有商品都加了alt和title的话，容易造成堆砌关键词，所以我一般是只加alt属性。

   - 图片大小声明：如果图片大小不做定义的话，页面需要重新渲染，就会影响到速度。

   - 非特殊性链接，链接地址一定要写入herf属性，做过SEO优化的人员都知道，蜘蛛目前对于js的支持很差，基本无法读取里面的链接地址。所以说用click事件是绝对不允许的，特别是一些重要的导航链接。

   - 网站结构呈扁平状树型，目录结构不宜过深，每个页面离首页最多点击不超过3次，过深不利于搜索引擎的抓取。

   - 做好404页面，一般会加首页链接及错误提示，并测试其返回状态码为404。 用户体验友好，可以留住用户不至于直接关闭页面；蜘蛛友好，可以返回抓取其他页面。

   - 重要内容不要用JS输出。蜘蛛不会读取JS里的内容，所以重要内容必须放在HTML里。

   - 尽少使用iframe框架。搜索引擎不会抓取到iframe里的内容，重要内容不要放在框架中。

## Vue中可以优化的点
- Vue库dist里面的Runtime-only比Runtime+Compiler小30%
- Vue的计算属性会根据依赖的data进行缓存
- keep-alive可以缓存常用组件
- Vuex中的getter也会根据依赖的state进行缓存
- v-for中唯一key的使用
- Vue全局错误处理errorHandle
- Vue路由懒加载
- Vue组件动态加载

## React中可以优化的点
- 在constructor改变this指向代替箭头函数和render内绑定this，避免函数作为props带来不必要的rerender
- shouldComponentUpdate，减少不不必要的rerender
- PureComponent高性能组件只响应引用数据的深拷贝
- 使用唯一key优化list diff
- 合并setState操作，减少虚拟dom对比频率
- React路由动态加载react-loadable
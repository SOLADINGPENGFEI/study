### css预处理器
css预处理器：用一种专门的编程语言，为CSS增加了一些编程的特性，将CSS作为目标生成文件，然后开发者就只要使用这种语言进行编码工作。

css存在的问题：语法不够强大，比如无法嵌套书写导致模块化开发中需要书写很多重复的选择器； 
没有变量和合理的样式复用机制，使得逻辑上相关的属性值必须以字面量的形式重复输出，导致难以维护。 
所以需要预处理器提供 CSS 缺失的样式层复用机制、减少冗余代码，提高样式代码的可维护性。

目前比较主流的三个处理器分别是 Less、Sass、Stylus

### Sass、LESS和Stylus的对比
安装 
1.sass的安装

首先安装ruby,建议安装到C盘中，安装过程中选择“Add Ruby executables to your PATH”

ruby安装成功后，启动Ruby的Command控制面板，输入命令

  gem install sass
1
回车后会自动安装好Sass

2.Less的安装

分为两种：客户端和服务器端安装。

a.客户端

只需要在官网载一个Javascript脚本文件主“less.js”，然后在我们需要引入LESS源文件的HTML的中加入如下代码：

<link rel="stylesheet/less" type="text/css" href="文件路径/styles.less">
<script src="文件路径/less.js" type="text/javascript"></script> 
1
2
b.服务器

利用node的包管理器（npm）安装LESS，安装成功后就可以在Node环境中对LESS文件进行编译。

首先安装node,安装成功后，启动node的Command控制面板，输入命令

  $ npm install less
1
回车后会自动安装好less

3.Stylus的安装

Stylus的安装和LESS在服务器端的安装很相似，先安装Node 。在Node的Command控制面板输入命令：

 $ npm install stylus
1
回车后会自动安装好stylus

# Sass、LESS和Stylus转换成css文件
1.sass

先在项目中创建一个Sass文件，此例中将其命名为“style.scss”，并且将其放在对应的项目样式中

启动Ruby的Command控制面板，找到需要转译的Sass文件

在对应的目录下输入下面的命令：

sass style.scss style.css
sass --watch style.scss:style.css
1
2
就会生成自动“style.css”文件，并自动更新对应的CSS样式文件

2.Less（了解）

在安装的Node JS环境下通过其自己的命令来进行转译。

 $ lessc style.less    
1
上面的命令会将编译的CSS传递给stdout，你可以将它保存到一个文件中：

$ lessc style.less > style.css 
1
3.Stylus(了解)

Stylus具有可执行性，因此Stylus能将自身转换成CSS。Stylus可以读取自“stdin”输出到“stdout”，因此Stylus可以像下面转译源文件：

$ stylus –compress  <some.styl> some.css   
1
Stylus也像Sass一样，同时接受单个文件和整个目录的转译。例如，一个目录名为“css”将在同一个目录编译并输出“.css”文件。

$ stylus css   
1
下面的命令将输出到“./public/stylesheets”：

 $ stylus css –out public/stylesheets  
1
还可以同时转译多个文件：

$ stylus one.styl two.styl 
1
如果你的浏览器安装了Firebug，那么可以使用FireStylus扩展。

$ stylus –firebug <path>

# 变量的处理
Less：变量处理方式–懒加载，所有 Less 变量的计算，都是以这个变量最后一次被定义的值为准。
Sass的变量处理方式和Stylus相同，变量值输出时根据之前最近的一次定义计算。这其实代表了两种理念：Less 更倾向接近 CSS 的声明式，计算过程弱化调用时机；而 Sass 和 Stylus 更倾向于指令式。

如果在Less中引入第三方样式库，可以通过重新配置变量来改变样式

优点：stylus和sass这样的处理会不容易受多个第三方库变量名冲突的影响，因为一个变量不能影响在定义它以前的输出样式

## css后处理器
css后处理器是对css进行处理，并最终生成css预处理器，它属于广义上的css预处理器
举例：css压缩工具（clean-css）,Autoprefixer(以Can I Use上的浏览器支持数据为基础，自动处理兼容问题)

# Autoprefixer:
优点：使用Css语法，容易进行模块化，贴近Css的未来标准
缺点：逻辑处理能力有限
# 框架举例
PostCss:是一个基于JS插件的转换样式的工具。PostCSS插件可以像预处理器，它们可以优化和Autoprefix代码；可以添加未来语法；可以添加变量和逻辑；可以提供完整的网格系统；可以提供编码的快捷方式等等
优点：
- 多样化的功能插件，创建了一个生态的插件系统
- 根据你需要的特性进行模块化
- 快速编译
- 创建自己的插件，且具可访问性
- 可以像普通的CSS一样使用它
- 不依赖于任何预处理器就具备创建一个库的能力
- 可以与许多流行工具构建无缝部署
# css选择器
分类：基础选择器、组合选择器、属性选择器、伪类选择器和伪元素等
- 基础选择器：
    id选择器（#footer），匹配所有id属性等于footer的元素。
    类选择器（.info），匹配所有class属性中包含info的元素。
    通用选择器（*），匹配任何元素。
    标签选择器（E），匹配所有使用E标签的元素。
    同级元素选择器（E~F ），匹配任何在E元素之后的同级F元素(CSS3)。
- 属性选择器:(E表示元素，attr表示属性，val表示属性的值。)
    E[attr]选择器,匹配所有具有attr属性的E元素，不考虑它的值。
    E[attr=val]匹配所有attr属性值为val的E元素。
    E[attr~=val]匹配具有attr属性且属性值用空格分隔的字符列表。
    E[attr|=val]匹配具有attr属性且属性值为用连接符（-）分隔的字符串，并以val开头的E元素。
    E[attr^="val"],属性attr的值以"val"开头的元素（CSS3）。
    E[attr$=“val”],属性attr的值以"val"结尾的元素（CSS3）。
    E[attr*="val"],属性attr的值包含"val"字符串的元素（CSS3）。
- 组合选择器
    多元素选择器（E, F），同时匹配多有E元素或F元素。
    后代选择器（E F），匹配所有属于E元素后代的F元素，E和F之间用空格分隔。
    子元素选择器（E > F）， 匹配所有E元素的子元素F。
    相邻选择器（E + F），匹配所有紧随E元素之后的同级元素F。
- 伪类选择器
    E:link, 匹配所有未被点击的链接.
    E:visited, 匹配所有已被点击的链接。
    E:active, 匹配鼠标已经将其按下，还没释放的E元素。
    E:hover, 匹配鼠标悬停其上的E元素。
    E:focus, 匹配获得当前焦点的E元素。
- 结构性伪类：E:nth-child(n), 匹配其父元素的第n个子元素，第一个编号为1。

## ！important属性
1、用于解决IE对某些CSS规范有偏差的情况. 
比如在IE中的效果总是和其他的浏览器如firefox,opera等相差2px,导致页面布局有错位， 这是因为IE对盒之间距离的解释的bug造成的，针对这种情况我们就可以利用!important来帮助解决。只有当同时出现两个同名的样式时，才可以这样用，此时IE浏览器是识别的 
2、如果有定义了一个样式A，比如font-size,你不打算让以后也叫样式A的覆盖掉这个font-size,也可以用 !important . 而如果新样式也用了!important 则还是会强制覆盖掉
## 优先级
！important >id选择器>class、属性、伪类选择器>标签选择器

权值越大优先级越高，权值相同，后定义的优先级较高，

浏览器查找元素是从右到左查找的，好处是为了快速过滤掉一些无关紧要的样式规则和元素

例如：DIV#divBox p span.red{color:red;}，浏览器的查找顺序如下：先查找html中所有class=’red’的span元素，找到后，再查找其父辈元素中是否有p元素，再判断p的父元素中是否有id为divBox的div元素，如果都存在则匹配上。
## 属性继承
CSS属性继承：外层元素的样式，会被内层元素进行继承。多个外层元素的样式，最终都会“叠加”到内层元素上。

不可继承的：display、margin、border、padding、background、height、min-height、max-height、width、min-width、max-width、overflow、position、left、right、top、bottom、z-index、float、clear、table-layout、vertical-align、page-break-after、page-bread-before和unicode-bidi。

CSS文本属性都会被继承的： 
color、 font-size、font-family、font-style、 font-weight 
text-align、text-decoration、text-indent、letter-spacing、line-height 
提示：<body>中的CSS属性，会被所有的子元素继承。

优先级就近原则，同权重的情况下样式定义最近者为标准，载入样式以最后载入的定位为准
## ID选择器和Class选择器的区别
ID选择器：每个元素只能有一个ID，每个页面只能有一个元素使用该ID

class选择器：多个元素可以共用相同类，一个元素可以有多个类
### 雪碧图原理
原理：把小图标合成一张大图，通过给元素的公共css设置background-image为该合成图，这样每个元素都会以该合成图为背景，而且页面也只加载一张合成图，然后再给每个元素单独微调其background-position。把多个请求合并成一个。

background-position

设置背景图像的起始位置。

background-position属性设置背景原图像（由 background-image 定义）的位置，意味着使用这个属性的前提是必须设置背景原图像background-image。

background-position的属性值:

方向值：x轴方向：left | right | center; y轴方向：top| bottom | center
使用百分比来设置属性值,以自身容器的长宽 减去 图片的长宽 乘以 百分比 所得的数值来确定图片的起始位置。
数值： X轴方向：x px ; Y轴方向：x px

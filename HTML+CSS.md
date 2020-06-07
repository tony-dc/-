### 一、认识HTML

####          1.   <!DOCTYPE html>

​          DOC->document  文本,TYPE->type类型

​          DOCTYPE声明必须在第一行,位于html标签之前.<!DOCTYPE>不是声明一个html标签，它是指web浏览器关于页面使用哪个HTML版本进行编写。

​         在 HTML 4.01 中，`<!DOCTYPE>` 声明引用 DTD，因为 HTML 4.01 基于 SGML。DTD 规定了标记语言的规则，这样浏览器才能正确地呈现内容(HTML5 不基于 SGML，所以不需要引用 DTD)

#####           2.<!---->标签

​                注释标签，添加对代码的解释，不会被浏览器解析,在html里标签里的!表示声明，“/”表示结束   

#####         3.单标签和双标签

​            单标签只有一个，双标签有两个，双标签用/结束，单标签没有，在HTML中单标签加与不加'/'都是可以正常解析的，但在HTML中不需要加，只有在XHTML中才必须加。

#####        4.HTML中的head标签

​           head标签用于定义文档的头部，它是所有头部元素的容器。head中的元素可以引用脚本(js知       识)，指示浏览器在哪里找到样式表、提供元信息等。文档的头部描述了文档的各种属性和信息，包括文档的标题、在 Web 中的位置以及和其他文档的关系等。绝大多数文档头部包含的数据都不会真正作为内容显示给读者

#####      5. head中的title标签

​           定义文档的标题，浏览器会以特殊的方式来使用标题，并且通常把它放置在浏览器窗口的标题栏或状态栏上。同样，当把文档加入用户的链接列表或者收藏夹或书签列表时，标题将成为该文档链接的默认名称（只强调重点即可，尽量把重要的关键词放在前面，关键词不要重复出现，尽量做到每个页面的<title>标题中不要设置相同的内容）

#####    6.head中的meta标签

​      meta标签提供网页的元信息，比如网页的描述和关键字，在html中meta标签是单标签，没有结束标签。

​      name属性：把content属性关联到一个名称。

​      content属性：定义与name属性相关的元信息（content属性始终要和name属性一起使用）

​       name为keywords时是网页描述，需要高度概括网页内容，切记不能太长，过分堆砌关键词，每个页面也要有所不同。

```html
<head>
    <meta charset="UTF-8">                  <!--char->字符,set设置集合，用哪款字符编码集合-->
    <meta  name='description' content="对该网页的描述" > 
    <meta  name='keywords'    content="关键字" >   
    <meta  name='author'    content="名称" >
    <title>标题内容</title>
</head>
```

##### 7.body 标签

 存放的是网页的身体部分也就是显示在页面中，用户能看到的部分。

####  body里面常用标签介绍：

  **1.div块标签** 

> ​      div元素也叫分区元素，在语意上不代表任何特定类型的内容。它可以被用来对其他元素进行分组，或者对具有相同特性的一组元素进行分组。它应该在没有其他语义元素可用时才使用。

​    **2.h系列标签**

> ​     h标签<h1-h6>呈现了六个不同级别的标题，h1级别最高，而h6级别最低正文标题h1标签，h1标签自带权重， 认为它最重要，一个页面有且最多只能有一个H1标签，放在该页面最重要的标题上面，如首页的logo上可以加H1标签。副标题用h2标签， 而其它地方不应该随便乱用 h 标题标签。<span style="color:red">（属于行内元素）</span>

   **3.p标签**

>   p标签属于文本段落标签，表示文本的一个段落。该元素通常表现为一整块与相邻文本分离的文本。<span style="color:red">（属于行内元素）</span>

  **4.blockquote标签**

> 引用元素(块级)，代表其中的文字是引用内容。

  **5.q标签**

> q标签的作用和blockquote标签的作用一致，不同的是q标签用于一个段落内的简短引用。 

  **6.pre标签**

> pre元素表示预定义格式文本。在该元素中的文本通常按照原文件中的编排，以等宽字体的形式展现出来，文本中的空白符（比如空格和换行符）都会显示出来。

  **7.span标签**

> span标签没有特殊语义，是短语内容的通用行内容器<span style="color:red">（属于行内元素）</span>

  **8.strong标签**

> strong标签表示文本十分重要，一般用粗体显示。

  **9.em标签**

> 着重元素，标记出需要用户着重阅读的内容。

**10.i标签**

> 用于表现因某些原因需要区分普通文本的一系列文本。例如技术术语、外文短语或是小说中人物的思想活动等，它的内容通常以斜体显示。

 **11.b标签**

> 给文字加粗,用于吸引读者的注意到该元素的内容上,尽管如此，你不应将 `<b>` 元素用于显示粗体文字，而是用css来控制

**12.a标签**

> a标签定义超链接，用于从一张页面链接到另一张页面。
>
> a 标签最重要的属性是 href 属性，它指示链接的目标。
>
> target属性：_blank在新窗口打开；__self在当前窗口打开。

**13.img标签** 

> 代表文档中的一个图像。
>
> src： 当前目录 -> ./ ; 上一级目录 ../

**14.video 视频**

> 视频标签，在文档中嵌入媒体播放器。支持的格式有Ogg、MP4、WebM。
>
> 可以在开始标签和结束标签之间放置文本内容，这样老的浏览器就可以显示出不支持该标签的信息。
>
> width：播放器宽度。单位只能为px，可以只写数值。
>
> height：播放器高度。单位只能是px，可以只写数值。
>
> src：资源地址。支持相对路径和绝对路径。
>
> controls：显示播放控件。如播放，暂停，音量，全屏等。默认不开启，开启：controls="controls"/controls。
>
> autoplay：是否自动播放。默认不播放，开启：autoplay=“autoplay”/autoplay
>
> loop：是否循环播放。默认不循环播放，开启：loop="loop"/loop
>
> poster：规定视频下载时和点击播放前显示的图像。
>
> preload：页面加载完成后是否载入整个视频。auto：载入，none：不载入，metadata:当页面加载完成后只载入元数据(如视频的大小，视频的长度等)。如果设置了autoplay属性则忽略preload属性。

**15.audio标签**

> 音频标签，在文档中嵌入音频内容。
>
> src：资源地址。可以是绝对路径也可以是相对路径。
>
> controls：显示控件。如播放，暂停，音量，全屏等。默认不开启，开启：controls="controls"/controls
>
> autoplay：**是否自动播放**。默认不播放，开启：autoplay=“autoplay”/autoplay
>
> loop：是否循环播放。默认不循环播放，开启：loop="loop"/loop
>
> muted：是否静音。默认关闭，开启：muted="muted"/muted
>
> preload：页面加载完毕后是否载入整个音频。auto：载入，none：不载入，metadata:当页面加载完成后只载入元数据(如视频的大小，视频的长度等)。如果设置了autoplay属性则忽略preload属性。

**16.embed标签**

> 引入外部视频或音频都可以，embed可以用来插入多种多媒体，例如：Midi、Wav、AU、MP3等。除此之外还可以加载其他的插件。

**17.ul无序标签**

> 无序列表元素，表示一个内可含多个元素的无序列表或项目符号列表。（li）

**18.ol标签**

> 有序列表元素，表示多个有序列表项，通常渲染带编号的列表。（li）

**19.dl标签**

> 定义了定义列表。
>
> dl标签常用于结合dt标签(定义列表中的项目)和dd标签(描述列表中的项目)（dt和dd）

​                               <span style="color:red">  **关于strong、em、i、b标签**</span>

> strong、em标签:需要强调时使用。strong标签在搜索引擎中能够得到高度的重视，它能突出关键词，表现重要的内容，em标签强调效果仅次于strong标签。



#### 20.  认 识 S E O

##### 为什么要合理使用标签？

​		为了网站SEO。

##### 什么是SEO？

​		SEO(Search Engine Optimization)，即搜索引擎优化。SEO是随着搜索引擎的出现而来的，两者是相互促进，互利共生的关系。SEO的存在就是为了提升网页在搜索引擎自然搜索结果中的收录数量以及排序位置而做的优化行为。而优化的目的就是为了提升网站在搜索引擎中的权重，增加对搜索引擎的友好度，使得用户在访问网站时能排在前面。

##### 为什么搜索引擎带来了SEO？

​		在搜索引擎网站的后台会有一个非常庞大的数据库，里面存储了海量的关键词，而每个关键词又对应着很多网址，这些网址是被称之为“搜索引擎蜘蛛”或“网络爬虫”程序从茫茫的互联网上一点一点下载收集而来的。随着各种各样网站的出现，这些勤劳的“蜘蛛”每天在互联网上爬行，从一个链接到另一个链接，下载其中的内容，进行分析提炼，找到其中的关键词，如果“蜘蛛”认为关键词在数据库中没有而对用户是有用的便存入后台的数据库中。反之，如果“蜘蛛”认为是垃圾信息或重复信息，就舍弃不要，继续爬行，寻找最新的、有用的信息保存起来提供用户搜索。当用户搜索时，就能检索出与关键字相关的网址显示给访客。一个关键词对应多个网址，因此就出现了排序的问题，相应的当与关键词最吻合的网址就会排在前面了。在“蜘蛛”抓取网页内容，提炼关键词的这个过程中，就存在一个问题：“蜘蛛”能否看懂。如果网站内容是flash和js等，那么它是看不懂的，会犯迷糊，即使关键字再贴切也没用。相应的，如果网站内容可以被搜索引擎识别，那么搜索引擎就会提高该网站的权重，增加对该网站的友好度。这样一个过程我们称之为SEO。

##### SEO的分类：

​		SEO分为白帽SEO和黑帽SEO。

​		白帽SEO：白帽SEO，起到了改良和规范网站设计的作用，使网站对搜索引擎和用户更加友好，并且网站也能从搜索引擎中获取合理的流量，这是搜索引擎鼓励和支持的。

​		黑帽SEO：黑帽SEO，利用和放大搜索引擎政策缺陷来获取更多用户的访问量，这类行为大多是欺骗搜索引擎，一般搜索引擎公司是不支持与鼓励的。

##### 白帽SEO是做什么的？

* 对网站的标题、关键字、描述精心设置，反映网站的定位，让搜索引擎明白网站是做什么的；
* 网站内容优化：内容与关键字的对应，增加关键字的密度；
* 在网站上合理设置Robot.txt文件；
* 生成针对搜索引擎友好的网站地图；
* 增加外部链接，到各个网站上宣传。

##### 为什么要做SEO？

​		提高网站的权重，增强搜索引擎友好度，以达到提高排名，增加流量，改善（潜在）用户体验，促进销售的作用。



#### 21.在使用标签的时候如何注意？

* `<title></title>`标签：只强调重点即可，尽量把重要的关键词放在前面，关键词不要重复出现，尽量做到每个页面的title标题中不要设置相同的内容。
* `<meta keywords>`标签：网页描述，需要高度概括网页内容，切记不能太长，过分堆砌关键词，每个页面也要有所不同。
  * `<meta description>`标签：网页描述，需要高度概括网页内容，切记不能太长，过分堆砌关键词，每个页面也要有所不同。
* `<a>`标签：页内链接，要加 “title” 属性加以说明，让访客和 “蜘蛛” 知道。而外部链接，链接到其他网站的，则需要加上 rel="nofollow" 属性, 告诉 “蜘蛛” 不要爬，因为一旦“蜘蛛”爬了外部链接之后，就不会再回来了。
* 正文标题要用`<h1>`标签：h1标签自带权重“蜘蛛” 认为它最重要，一个页面有且最多只能有一个H1标签，放在该页面最重要的标题上面，如首页的logo上可以加H1标签。副标题用<h2>标签, 而其它地方不应该随便乱用 h 标题标签。
* `<img>`应使用 "alt" 属性加以说明。
* 表格应该使用`<caption>`表格标题标签，caption 元素定义表格标题。caption 标签必须紧随 table 标签之后，您只能对每个表格定义一标题。
* `<br>`标签：只用于文本内容的换行。 
* `<strong>`、`<em>`标签 ：需要强调时使用。`<strong>`标签在搜索引擎中能够得到高度的重视，它能突出关键词，表现重要的内容，`<em>`标签强调效果仅次于`<strong>`标签。
* `<b>`、`<i>`标签：只是用于显示效果时使用，在SEO中不会起任何效果。
* 尽量少使用`<iframe>`框架,因为“蜘蛛”一般不会读取其中的内容。





### 二、认 识 C S S

#####  1.什么是css

> ​    css指的是层叠样式表，Cascading Style Sheets。负责美化页面。
>
> ​     css的基本概念：
>
> ​        功能符：值以函数的形式指定（就是被括号括起来的那种）。
>
> ​	 	属性：我们对一个元素的描述。
>
> ​		 属性值：属性冒号后面的所有内容统一称为属性值。
>
> ​		 声明：属性名加上属性值就是声明。
>
> ​		 声明块：生命快时花括号包裹的一些列声明。

#####  2.css的引用方式

> ​                1.内联方式：写在style标签里面
>
> ​                 2.外联样式：通过link标签引入
>
> ​                  3.行内样式：直接写在标签里

  **3.元素/标签命名的基本格式**  

> class命名(别称：类名)，可以有多个
>
> id命名。只能有一个(规范)，防止操作元素时失效。

#####    4.css样式设置的基本格式

> 选择器+{属性名+：+属性值}  -> 声明块
>
> 属性名+：+属性值 -->声明

#####    5.常用样式类别：

* 尺寸样式：

​      width: ：宽

​       height：高

-  位置样式

​           水平位置：

​                  margin-left

​                   margin-right

​             垂直位置

​                    margin-top 顶部外边距

​                    margin-bottom 底部外边距

装饰样式：

* ​    background-color（背景）

文字样式：

*    文字大小：font-size
* ​    文字字体：font-family
* ​    文字颜色：color

#####      6.网页文档结构分析

* 一个html文档就是一个树状结构。
* 后代选择器：后代元素选择器是一个空格，空格前后各有一个选择器。选中一个元素的指定后代元素(空格后的选择器指向的所有后代元素)。
* 子代选择器：后代选择器是一个大于号，大于号前后各有一个选择器。选中一个元素的指定子代元素(大于号后面的选择器指向的元素，**只包括子代，不包括孙代**)。
* 相邻选择器：相邻元素选择器是一个+号，+号前后各有一个选择器。选中一个元素的指定相邻元素(+号后面的选择器指向的元素)。<span style="color:red">（指自己不算，选中上面有同元素哥哥的元素）</span>
* 兄弟元素选择器：兄弟元素选择器是一个~号，~号前后各有一个选择器。选中一个元素的指定兄弟元素(~号后面的选择器指向的元素)。<span style="color:red">（指自己不算，同代中所有和自己相同的元素）</span>

#####      7.样式优先级：

> 行内样式：权重1000
>
> ID选择器，单个权重100
>
> 类名选择器，属性选择器，伪类选择器，单个权重10
>
> 标签选择器，伪元素选择器，单个权重1
>
> 通配符选择器，关系选择器(+，>，~，空格)，否定伪类，权重0

###    



###  三、CSS中的盒模型

#####  1.什么是盒模型:

> 英语(box module)是w3c规定一个浏览器如何渲染，显示一个元素。

#####  2.盒模型分类:

> 块级元素盒模型和行内元素盒模型。

 

##### 3.标准盒模型的概念分析：

* width/height：块级元素的width和height值在标准盒模型下，定义了一个块级元素能够存放内容的区域大小，元素的内容从width和height的左上角原点开始排列内容。

  > 颜色详解：rgb（）rgb表示三原色红、绿、蓝。rgb里填三个数值，用逗号隔开例如：rgb(12
  >
  > ,36,85) 每个数值都在0-255之间。
  >
  > rgba（）rgba中的a表示透明度，值在0-1之间，0表示完全透明，1表示不透明
  >
  > hsla() ： H 色调，取值在0-360之间；S饱和度，取值在0%-100%之间；L亮度，取值在0%-100%之间；A表示透明度，取值在0-1之间。

#####  4.盒模型一共分为两类：怪异盒模型和标准盒模型

#####  5.内容区:

>  (width，height)：规定元素里盛放内容区域的大小，内容默认从元素的左上角开始排列

#####   6.边框(border-box)分为：

​     边框样式写法 -> border: border-width（边框宽度） border-style （边框样式）border-color（边框颜色）; 

​       <span style="color:red">border-style的可选值: dotted[圆点虚线]  dashed[实线虚线]  double[双实线]  solid[实线] ，groove[3D凹槽边框]，ridge[3D垄状边框]，inset[3Dinset边框]，outset[3Doutset边框]</span>

​       <span style="color:red">border-width可选值: thin[细边框]，  medium[中等边框]，  thick[粗边框] 、具体像素值</span>

 border（上，下，左，右）边框设置： ->宽度  样式  颜色（如果不加具体那位置加则默认全部加外边框，他不能用复合属性设置）设置border样式时，如果不设置宽度，默认宽度是3px。如果不设置颜色，默认和字体颜色一致。如果不设置边框样式则默认没有边框。

​      **三角形案例（通过边框）**

```html
 <style>
        .box {
            margin: 0 auto;
            width: 0px;
            height: 0px;                                 //宽度和高度需要设置为0
            border: 5px solid transparent;               //需要让其中三边显示透明
            border-left-color: blue                      //给其中一边显示颜色
        }                    //三角形位置对应（left->指向右）（top->指向下……相反呈现）
    </style>
</head>
<body>
    <div class="box">
    </div>
```

#####   7.内边距区(padding box):

> 在边框和内容区域之间添加一个透明区域。
>
> 复合写法 -> padding:  像素值； 四周的透明区域大小。
>
> ​					 padding: 上下     左右；
>
> ​					padding: 上  左右    下；
>
> ​					padding：上 右 下 左；
>
> 单例样式：
>
> ​	左内边距 -> padding-left：像素值；
>
> ​    右内边距 -> padding-right：像素值；
>
> ​	下边距 -> padding-bottom：像素值；	
>
> ​	上边距 -> padding-top：像素值；

##### 8.怪异盒模型的整体概念

块元素在网页内容中实际占据空间的大小在怪异盒模型和标准盒模型下是不一样的：

* 标准盒模型下：

  > 标准盒模型的实际宽度=width+左padding+右padding+左border+右border
  > 标准盒模型的内容区宽度=width

* 怪异盒模型下：

  > 怪异盒模型的实际宽尺寸=width
  > 怪异盒模型的内容区宽尺寸=width-左border-右border-左padding-右padding

* 高度同理可得。

##### 9.怪异盒模型的使用场景

如果不想因为改变padding的时候盒子的大小也会跟着变化的话就可以使用怪异盒模型,而如果想让盒子的大小被padding撑开的话就可以使用标准盒模型

##### 10.父子元素外边距合并现象

>  大盒子中嵌套小盒子，如果给小盒子添加margin-top属性，则会出现大盒子和小盒子一起向下移动的现象。
>
> 解决办法：给父元素设置border或者padding。
>
> ```html
> .box {
>             margin: 0 auto;
>             width: 100px;
>             height: 100px;
>             background-color: red;
>             border: 1px solid red                   //必须要加个外边框或者padding值
>         }
>         
>         .box2 {
>             margin: 50px auto 0;
>             width: 50px;
>             height: 50px;
>             background-color: blue;
>         }
> ```
>
> 

##### 11.兄弟元素外边距合并现象

> 兄弟元素之间，垂直方向外边距如果都是正数不会叠加，而会发生外边距合并现象，并且外边距最终会取数值较大的。
>
> 例
>
> ```html
>  .box {
>             margin: 0 auto 100px;
>             width: 100px;
>             height: 100px;
>             background-color: red;
>         }
>         
>         .box2 {
>             margin: 200px auto 0;
>             width: 100px;
>             height: 100px;
>             background-color: blue;                //最终外边距值为200px
>         }
> ```

####   

### 四、 行 内 盒 模 型

#####     1.什么是行内盒模型：

​                 行内盒模型指的是行内元素的盒模型，行内盒模型指的是如何排版行内元素的一套规则。  

#####      2.行内元素和块级元素的不同

* 行内元素分为可替换的行内元素和不可替换的行内元素

  > 可替换的行内元素指的是内容可以直接在代码里看到的：文字
  >
  > 不可替换的行内元素指的是内容不能再代码里显示出来的，比如视频，音频

- 不可以替换行内元素与块级元素的区别

  ​    1.不能设置宽高，宽高由里面的内容撑开

​           2.不支持上下的margin、padding、border，支持左右的margin、padding、border

​            3.可以和其它行内元素并排显示

-   可替换行内元素与块级元素的区别 

  ​    1.可替换的行内元素支持设置宽高

  ​    2.可替换元素支持margin、padding和border。但是margin不支持使用auto居中

#####    3.可替换行内元素：文字

​              font-size：font-size设置的值并不是文字真实的大小，而是文字内容所占的区域大小，如果不设置font-size，浏览器会默认继承父级的文字大小，font-size设置除了用 px像素外，还可以用em，1em表示同等大小（数字增加是成倍数增加）。

#####    4.不改变文字大小，如何让行内元素位置更大：行高

​    使用line-height：

> 1. line-height是行高的意思。行高等于font-size+上下间距。
>
> 2. 在没有可替换元素的情况下line-height决定了一行文字在页面中占据的距离。
>
> 3. 行高可以是具体的像素值也可以是一个数值，在设为数值的情况下，表示当前行内元素字体大小的几倍，类似于em但是没有单位。行高也可以设置成em值。

#####    5.那在有替换元素的情况下呢？

> 1. 如果一行内有文字也有可替换元素，比如图片。这时候本行文字距上一行文字之间的间距被拉大了，这是为什么呢？
> 2. 因为每一行都有一个行框，这个东西看不见摸不着，但是存在。在只有文字的情况下，行框和line-height一样高。如果文字内加入了图片或视频、音频，那么这个行框就被撑大了。
> 3. 同时我们看到图片和文字并不是对齐的，他们之间有一小点差距。为什么呢？因为行内元素默认都是基线对齐的。可替换元素它没有基线，那怎么办呢？它就会去找文字的基线。行框被撑大了所以这行文字距上一行文字之间的距离也被放大了。

#####     6.  如果我们想让文字和图片在垂直方向上对齐该怎么办呢？

使用一个叫做vertical-align的属性。vertical-align表示垂直对齐方式，vertical-align只能加给替换元素！！！！它有这样几个值：

> vertical-align：
>
> ​	middle: 文字的中线和替换元素的高的一半对齐
>
> ​	top: 图片的顶部和文字的行高最顶部对齐
>
> ​	bottom：图片的底部和文字的行高最底部对齐
>
>    vertical-align的值也可以是数值
>
> 单行不同文字大小、行高对行内盒模型的影响
>
> > 若行内盒模型里只有文字这一种元素且同一行里文字的大小不一致，则行框大小等于line-height最大的行内元素。且行盒里的文字默认是基线对齐的。

#####     7. 文 本 样 式 

​       文本首行缩进：text-indent：值可以是px（像素）也可以是em（推荐使用）

​       文本对齐方法：text-align：（left，center，right,justify=>两端对齐）

​       文本装饰（下划线）：none（默认），underline（下划线），overline（文本上的一条线），	  line-through[贯穿线或者叫删除线]

###    五、CSS中的显示样式

#####         css样式中从上到下遵循的样式添加顺利为：

> 1.显示样式（例如display）
>
> 2.宽高样式（例如 width，height，border）
>
> 3.背景样式（例如background颜色和图片）
>
> 4文字样式
>
> 5.css3样式

#####      1.显示样式（display）：三个值

​                   block：块级盒模型

​                   inline：行内盒模型

​                   in-block：行内块级盒模型

##### 2.三种值的意思、作用和区别：

​      **1.display：inline：就是将元素显示为行内元素， inline元素的特点是**<span style="color:red">（**当行内盒模里面元素用display：inline一行排列时，取消间距的2种方式，1.给父元素设置font-size：0，子元素设置正常font-size字体大小。2.元素呈一行排列，让其不产生空格**）</span>

​           和其他元素都在一行上；<span style="color:red">高，行高及顶和底边距不可改变；宽度就是它的文字或图片的宽度，不可改变。</span>span, a, label, input, img, strong 和em是inline元素的例子 

```css
![inline2](D:\前端软件\前端学习笔记\思维导图\思维导图\img\inline2.png)div {
        width: 150px;
        height: 50px;
        border: 1px solid red
    }
    
    span {
        display: inline;
        border: 1px solid blue;
    }
```

![inline   block](D:\前端软件\前端学习笔记\思维导图\思维导图\img\inline   block.png)

![inline](img\inline.png)



​     **2.display：block：就是将元素显示为块级元素   ，block元素的特点是**

​      总是在新的一行显示,  独占一行， 高度，宽度，以及底和定边距都可以控制， 宽度缺省是它的容器的100%，除非设定一个宽度 块级元素例如:div,h,form,ul,li

​                                                              ![block](img\block.png)

​    **3.dispaly：inline-block:将对象呈递为内联对象，但对象的内容作为块对象传递， 旁边的内联对象会被呈递在同一行内，允许空格 ，inline-block的特点是：**

​            将对象呈递为内联对象，但是对象的内容作为块对象呈递。旁边的内联对象会被呈递在同一行内，允许空格。(准确地说，应用此特性的元素呈现为内联对象，周围元素保持在同一行，但可以设置宽度和高度地块元素的属性) 

![inline2](D:\前端软件\前端学习笔记\思维导图\思维导图\img\inline2.png)

​                                                                ![inline-block](img\inline-block.png)

4. **inline和block可以控制一个元素的行宽高等特性，需要切换的情况如下**：

> 让一个inline元素从新行开始；
> 让块元素和其他元素保持在一行上；
> 控制inline元素的宽度（对导航条特别有用）；
> 控制inline元素的高度；
> 无须设定宽度即可为一个块元素设定与文字同宽的背景色。

#####   5.display:none 隐藏，

  <span style="color:red">**display：none与 opacity的区别:display：none浏览器不会渲染，压根消失的元素不会影响后面元素的布局，但是opacity他虽然消失，但是它本身所占据的空间还在，后面的元素无法占用，只能往后面排列**</span>

![display-none](D:\前端软件\前端学习笔记\思维导图\思维导图\img\display-none.png)

#####     6.浏览器的兼容问题，如下图：

![浏览器兼容写法](D:\前端软件\前端学习笔记\思维导图\思维导图\img\浏览器兼容写法.png)

7.清除默认样式

![清除默认样式规则](D:\前端软件\前端学习笔记\思维导图\思维导图\img\清除默认样式规则.png)

###  六、背 景 样 式（background）

#####     1.opacity和display的区别

-  opacity设置的是透明度，值的范围是0~1，0代表完全透明，1代表不透明
- display为none，浏览器就不会渲染这个元素。（一个元素设置为display为none后想让他在显示出来使用，display:block）

#####     2. 背景颜色显示部分为内容部分+padding+border

​       插入背景图片：background-image:url(’图片地址‘)（背景图片支持的格式：.jpg，.png，.gif，.webp）

```css
div{
 background-image: url('./images/pic.jpg'),url('./images/pic.jpg');/*可以插入多个图片*/
}
```

  浏览器的渲染层级：

   1.内容层

   2.边框层

   3.背景图片

   4.背景颜色

 背景图片为什么会重复显示：

> 浏览器发现图片比盒子小就会让图片平铺把盒子占满

#####   3.设置背景图片是否重复：background-repeat

```css
div{
 background-repeat:
 	no-repeat /*垂直方向和水平方向都会重复*/
     repeat-x /*水平方向平铺*/
     repeat-y /*垂直方向平铺*/
     repeat /*垂直方向和水平方向都会重复*/
     ;
}
```

#####   4.设置背景图片尺寸大小：background-size

（设置完背景图片不平铺之后发现图片不会出现在border内，为什么？答案：背景图片在设置平铺的时候会先在内容区显示一张图片，然后再去平铺。）

​    使用bacnground-size属性就可以把图片拉大，有俩个值（background-size：width背景图片的宽 height背景图片的高；宽高可以设置为像素px值，也可以设置为百分比：）

```css
div{
 width:500px;
 height:500px;
 background-size: 500px 500px;/*支持，宽度和高度相等，也就是等与铺满内容区*/
 background-size:50% 50%;/*同比例缩放*/
 background-size:350px;/*只写一个值的时候宽缩放至350px，高等比例缩放*/
}
```

​    background-size还有两个比较特殊的值：cover、contain

```css
div{
 width:500px;
 height:500px;
 background-size: 
     cover/*图片一直缩放到铺满整个内容区域-可能会失真*/
     contain/*如果一条边缩放到铺满内容区域后另一条边停下来不在继续缩放*/
     ;
}
```

5.背景图片默认是从padding左上角开始排列，如何改变它的起始点：background-origin（背景原点）

```css
div{
    background-origin:
        padding-box/*背景图片相对于内边距来定位*/
        border-box/*背景图片相对于外边距来定位*/
        content-box/*背景图片相对于内容区域来定位*/
        ;
}
```

6.背景图片裁剪：background-clip

```css
div{
    background-clip:
        content-box/*只显示内容区部分的图片和颜色*/
        border-box/*显示border+padding+内容区的背景图片和背景颜色*/
        padding-box/*显示padding+内容区的背景图片和背景颜色*/
        ;
}
```

7.overflow属性：设置超出之后如何显示

> ​        hiddle：超出部分隐藏
>
> ​         visible：超出之后正常显示（默认）
>
> ​         scroll：不管内容超不超出都显示一个滚动条
>
> ​         auto：内容不超出的时候不显示滚动条，内容超出则显示滚动条

8. 如何不让背景图片不跟随内容区域滚动:background-attachment

> ​         scroll：不随内容区域滚动，而是定在起始位置（默认）
>
> ​         local：会随内容滚动而滚动
>
> ​        fixed：在窗口定义，元素区域随高度变化排列不一样

9.背景图片的复合式写法：

```css
div{
    background:color image  repeat attachment position/size/*位置和大小需要使用/分隔开*/
      background：red url('') no-repeat local -400px -300px/100% 100%/*例子*/
}
```

 background是一个 [简写属性](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Shorthand_properties)，可以在一次声明中定义一个或多个属性：[`background-clip`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-clip)、[`background-color`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-color)、[`background-image`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-image)、[`background-origin`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-origin)、[`background-position`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-position)、[`background-repeat`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-repeat)、[`background-size`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-size)，和 [`background-attachment`](https://developer.mozilla.org/zh-CN/docs/Web/CSS/background-attachment) 

###   



### 七：浮动（float）

#####    1.什么是浮动：

 当我们给一个元素设置浮动以后，该元素就在原来的位置飘起来了。浮动最初是为了让文字在图片周围的环绕效果。

​       浮动的特点：

​              1.浮动元素之间不会彼此覆盖.

​              2.浮动元素的下面绝对不允许出现文字内容

​             3.如果浮动元素的前面有不浮动的元素，那么该元素会原地浮起，

​             4.浮动会自动把一个元素转化为块元素

​             5. <span style="color:red;font-size:18px">如果父元素的宽度不足以容纳所浮起来的元素宽度，那么会一次往下排列，不会重合</span>

​    例：

​     

```css
 div{
      width:400px;
      height:400px
         }
div>ul{
     width:100%；
     height：100%
}
div>ul>li{
    width:100%;
    height:100%;                 /*浮动失效，这是因为ul的宽度和li的宽度一致，所以当多个                                            li元素时，li元素无法正常浮动到上一个li元素的的右侧排列*/
    float:left;
}                            
```

​        6. 浮动float的两个值：左浮动（left），右浮动（right）

​        浮动的样式原理是（left）：如下案例

```css
  .father {
        margin: 50px auto;
        width: 500px;
        border: 1px solid green
    }
    
    div {
        width: 100px;
        height: 100px;
        background-color: red;
    }
    
    .box1 { 
        float: left              /*当我给第一个元素设置浮动时，第一个就会飘起来，不会占用                                 原来的位置，第二个没设置浮动的会往上移，第三个也会往上移*/
    }
    
    .box2 {
        float:left;
        width: 200px;           
        background-color: blue;/*同理给第二个设置左浮动，他会飘起来，但是不会覆盖第一个浮                                       动，会排在它的后面*/
    }
   .box3 {
        float:left;
        width: 300px;
        background-color: yellow;
    }                           /*同理给第三个设置左浮动的时候，如果父元素宽度够就会浮起来依次排到后面，否则会往下排列
```

​     浮动的样式原理是（右）：如下案例

```css
  .father {
        margin: 50px auto;
        width: 500px;
        border: 1px solid green
    }
    
    div {
        width: 100px;
        height: 100px;
        background-color: red;
    }
    
    .box1 {
        float: right          /*当我给第一个元素设置右浮动时，第一个就会飘起来往右边排列，不会占用原来的位置，第二个没设置浮动的会往上移排在左边最上面，第三个也会往上移*/
    }
    
    .box2 {
         float: right; 
        width: 200px;
        background-color: blue;
    }                         /*给第二个设置右浮动，则会从右边依次往左排列，不会覆盖第一个右浮动，*/
    
    .box3 {
        float: right; 
        width: 300px;
        background-color: yellow;
    }                      /*同理，第三个也会依次往左排列，不会覆盖之前右浮动的元素，如果浮动元素宽度超出父元素宽度，则超出的那个元素会往右下排列
```

  总结：依照上面的案例，左右浮动，根据浮动元素不会覆盖，会按照浮动原理去浮动。当浮动的元素高度和宽度大于为浮动元素导致未浮动元素上移，如果里面有文字，则会挤到浮动元素下边排列

#####   2.浮动样式父元素高度塌陷

​      当一个父元素没有设置高度，高度由子元素高度撑开，当其子元素设置浮动时，被撑开的父元素高度就会塌陷，导致整个网页布局紊乱。这就叫浮动样式父元素高度塌陷。

​     例

```css
  .father {
        margin: 50px auto;
        width: 500px;
        border: 1px solid green      /*没有设置高度，其高度由子元素撑开*/
    }
    
    div {
        width: 100px;
        height: 100px;
        background-color: red;
    }
    
    .box1 {
        float: right
    }
    
    .box2 {
        float: left;
        width: 200px;
        background-color: blue;
    }
    
    .box3 {
        float: right;
        width: 100px;
        background-color: yellow;
    }                       
```

​           图1：浮动前

![float](img\float.png)

​       图2：浮动后

​                    ![float2](img\float2.png)

#####  3.如何解决浮动元素高度塌陷问题：<span style="color:red">（一定是块级元素）</span>

​       **1、第一种方案是给父元素加BFC（块级格式化上下文），给父元素设置以下属性之一即可（可以理解为，当父元素加了BFC，就等于给父元素加了个虚拟边框，高度由浮起来的元素撑开）**

​                overflow：hidden/auto/scroll （显示自动或者隐藏都可以）

​               display：inline-block（设置成块级元素）

​                float：left；（给父元素增加浮动）

​                position:absolute(绝对定位)

​      **2、第二种方案是：幽灵元素->给父元素的子元素末尾增加一个空的块元素**

​                 1.如上面案列所示：直接在子元素加一个空的div元素，并且在它的样式中设置clear:both.

​                 这样虽然能解决塌陷问题但是最大的缺点就是：会破坏页面的文档结构。

​                  2.有更好的办法：就是给父元素加一个空的伪元素，把它的属性设置为clear：both，这样就能很好的解决塌陷的问题，并且不会破坏文档结构<span style="color:red">（推荐使用）</span>

   例

```css
 .father {
        margin: 50px auto;
        width: 500px;
        border: 1px solid green;
    }
    
    .father:after {
        content: '';
        clear: both;
        display: block;                     /*加一个块级伪元素*/
    }
    
    div {
        width: 100px;
        height: 100px;
        background-color: red;
    }
    
    .box1 {
        float: left;
    }
    
    .box2 {
        float: left;
        width: 150px;
        background-color: blue;
    }
    
    .box3 {
        float: left;
        width: 200px;
        height: 200px;
        background-color: yellow;
    }
```

![float-after](img\float-after.png)

#####  4.清 除 浮 动 （clear）

​    什么是清除浮动：就是当元素设置了浮动以后，下面的元素如果设置清除浮动，那么该元素将不会跑到浮起来元素的重合位置，而是相当于伸出一只手挡住了下面元素上移的空间，（如果左右同时清除，那么将会按照那个高度最大就按那个高度挡住原则）例

```css
 .father {
        margin: 50px auto;
        width: 200px;
        border: 1px solid green;
    }
    
    div {
        width: 50px;
        height: 50px;
        background-color: red;
    }
    
    .box1 {
        float: left;
    }
    
    .box2 {
        float: right;
        width: 60px;
        height: 60px;
        background-color: blue;
    }
    
    .box3 {
        clear: both;
        width: 70px;
        height: 70px;
        background-color: yellow;
    }
```

![clear-float](img\clear-float.png)





### 第八章 圆角样式（border-radius）、渐变色

​      **一.boeder-radius：圆角样式，可以单个设置**

> ​     border-top-left-radius:左上
>
> ​    border-top-left-radius:右上
>
> ​    border-bottom-left-radius:右下
>
> ​    border-bottom-left-radius:左下

​        border-radius可以复合式设置，

> ​      四个值:上左，上右，下右，下左
>
> ​      三个值：左上 右上左下 右下
>
> ​      两个值：左上右下  右上与左下

  2.border-radius的属性值可以分为两段，由一个反斜杠 / 隔开，设置反斜杠前面的值为横轴值，后面的值为纵轴值，椭圆的写法与圆角类似，反斜杠前后皆为独立的。（横轴和纵轴值分开独立可以设置一个也可以是多）例

```css
    section{
          margin:50px auto;
          width: 400px;
          height: 400px;
          background-color: red;
          border-radius: 200px/50px         
      }
```

![椭圆](D:\前端软件\前端学习笔记\思维导图\思维导图\img\椭圆.png)

3：通过圆角边框设置成圆形的方法：都设置成50%或者为元素宽高的一半；border和border-radius没有任何关系.当圆比较大的时候,也只会影响单一设置的那个角,不会影响其他角

4.如果想要两边是圆上下不变,可以设置圆角为高度的一半,即可实现.

**二、渐变色**

​      1、渐变色分为线性渐变（linear-gradient）和径向渐变（radial-gradient），渐变色就是一个背景

​         线性渐变的属性值为：linear-gradient（起始位置   ( 颜色)    0%（作用的范围） , 颜色   100%（作用的范围））

​      渐变色的渲染方向值：

> ​      to bottom：默认是从上到下，
>
> ​      to top ：从下到上
>
> ​      to left：从右到左
>
> ​      to right：从左到右

​     同时方向值也可以是角度值：0 deg……360deg都是可以的，当然为0deg时，也就是从下往上渲染,

然后随着度数越来越大,会顺时针旋转

```css
div{
    linear-gradient(
    	to bottom,     //从上到下
    	/*这段代码的效果和上面的一模一样,其中0%表示红色最浓的地方，百分之百表示紫色最浓的地方,中间的颜色由计算机帮我们生成,上一段代码没有写这个值那么浏览器解析的时候会自动帮我们加上*/
    	red 0%,  
    	purple 100%
    )
}
```

如果设置三个值

```css
div{
    linear-gradient(
    	to bottom,
    /*浏览器自动分配 一共是100% 那么红色是0% 紫色是50% orange是100%*/
    	red,
    	purple,
    	orange
    )
}
```

我们如果需要调整里面的颜色值,那就是

```css
div{
    linear-gradient(
    	to bottom,
    	red,                                                         /*刚开始默认是为0*/
    	purple 20%,                                                  /*到20%变为紫色
    	orange                                                       /*到最后过渡到橙色100%
    )
}
```

设置的值表示何时完全变为某个颜色,中间就是渐变的过程,

2、径向渐变 的属性值：radial-gradient：用来展示由原点（渐变中心）辐射开的颜色渐变。只能为标准的圆形或椭圆。径向渐变类似与一个同心圆，一层一层往外散开。

```css
div{
    background-image:
        radial-gradient(
        	形状(ellipse椭圆，circle圆)和圆心的位置，（元素半径的一半）
            渐变的尺寸大小
        )
        ;
}
```

重复渐变色和渐变色重复

repeating-linear-gradient（45deg，red 0，35.4px blue，35.4px blue，70.7px yellow）





### 第九章：表 单 元 素

  1.表单元素的作用是收集用户输入的信息，并向后台发送这些数据

​       表单元素：

​     

```css
<form method='' action=''>
 <!--
		创建一个表单元素，把用于收集用户信息的元素写在里面
		method:表示向后台发送请求的方法：常用 get请求 post请求
		action:填写后台的路径 例如: https://www.baidu.com
	-->
</form>
```

表单里面最重要的元素：input（输入框）

```html
<!--input是一个单标签，同时是一个行内块元素，里面有两个个非常重要的属性 type：决定了input标签里的数据类型，type属性默认为text(文本类型)，name属性，这项数据应该保存在哪里-->
<input type="" >
<!--例：下边的例子表示这个input里填的是任意文本包括数字，文字，字母同时这一input里填的数据最终传到后台以后，后台明确的知道这个数据是用户的名称-->
<input type="text" name="名称">
```

type的类型种类：

-   type='text'  文本类型：可以是文字也可以是数字

  ```html
  <!--placeholder占位符，提示用户,maxlength最多可以输入多少字，minlength最少几个文本-->
  <input type="text" name="name" placeholder="请输入您的姓名" maxlength="5" minlength="2" >
  ```

- type='password'密码类型

  ```html
  <!--输入的密码会被遮盖-->
  <input type="password" name="usrpassword" placeholder="请输入您的姓名" maxlength="5" minlength="2" >
  ```

- type='number'：数值类型

```html
<!--输入的只能是数字，value默认值，min最小值，max最大值，step一次加多少不能为负，input元素会根据max的值设置宽度-->
<input type="number" name="age" placeholder="0" value="10" min="0" max="100" step="10">
```

- type='range':数字输入是滑块

  ```html
  <!--数字滑块，placeholder无效，默认值value-->
  <input type="range" name="volume" placeholder="请选择音量" min="0" max="100" step="10" value="10">
  ```

  date：选择年月日

  ```html
  <!--选择年月日placeholder无效，value必须以横岗链接，min最小日期，max最大日期-->
  <input type="date" name="date" placeholder="请选择日期" value="2017-06-10" min="2017-06-10" max="2017-10-20">
  ```

  time：选择时分

  ```html
  <!--选择小时：分钟，需要显示秒的话写上step，max最大时间，min最小时间-->
  <input type="time" name="appt-time" value="15:30" max="23:59" min="13:00" step="5">
  ```

  week：显示年份第几周

  ```html
  <!--选择小时：分钟，需要显示秒的话写上step，max最大时间，min最小时间-->
  <input type="time" name="appt-time" value="15:30" max="23:59" min="13:00" step="5">
  ```

  month：显示年和月

  ```html
  <!--值的写法 2019-01 2019年1月-->
  <input type="month" name="month" max="2019-12" min="2019-01" value="2019-05">
  ```

  datetime-local：显示年月日时分秒

  ```html
  <!--值的写法 2019-06-14T00:00:00-->
  <input type="datetime-local" name="datetime-local" value="2019-10-22T09:30:20" max="2019-10-22T00:00" min="2019-10-22T24:00" step="1"> 
  ```

  color：选择颜色

  ```html
  <!--颜色值不能用简写，调用系统自带的颜色选择器-->
  <input type="color" value="#cccccc">
  ```

  file：文件输入

  ```html
  <!--上传文件，包括视频、音频、图片 multiple开始多个上传-->
  <input type="file" multiple>
  ```

  使用input标签可以模拟其他的内容

  普通按钮

  ```html
  <!--type值为button时元素显示为一个按钮，按钮里的文字由value值提供-->
  <input text='button' value='我是一个按钮'
  ```

  提交按钮

  ```html
  <!--按钮点击之后会提交表单数据-->
  <input type="submit" value="提交">
  ```

  单选框

  ```html
  <!--注意在模拟单选的时候name值一定要相等-->
  <input type="radio" name="sex" value="lu">露望舒 
  <input type="radio" name="sex" value="female">武藤·纯子<br>
  ```

  多选框

  ```html
  <input type="checkbox" name="wife" value="chunzi">武藤·纯子 
  <input type="checkbox" name="wife" value="zhuang" checked>庄晓曼
  <input type="checkbox" name="wife" value="lu">露望舒 
  <input type="checkbox" name="wife" value="fang">方敏<br>
  ```

  扩大按钮的选中区域

  ```html
  <!--label里for属性的值一定要和input的id值一样-->
  <input id="chun" type="checkbox" name="allwife" value="chunzi">
  <label for="chun">武藤·纯子</label>
  ```

  select下拉列表

  ```html
  <!--name表示这个下拉框的名字-->
  <select name="wife">
  	<option value="lu">露望舒</option>
  	<option value="chun">武藤·纯子</option>
  	<option value="fang">方敏</option>
  	<option value="zhuang" selected>庄晓曼</option>
  </select>
  ```

  分组下列选项

  ```html
  <!--select元素是行内块元素-->
  <select name="otherwife">
  	<optgroup label="可爱型">
  		<option value="wang">露望舒</option>
  	</optgroup>
  	<optgroup label="清纯型">
  		<option value="zi" selected>武藤·纯子</option>
  	</optgroup>
  	<optgroup label="御姐型">
  		<option value="xiaoman">庄晓曼</option>
  		<option value="min">方敏</option>
  	</optgroup>
  </select>
  ```

  多文本输入区域

  ```html
  <!--行内块元素  rows行 cols列-->
  <textarea name="article" rows="10" cols="10" placeholder="输入你想输入的内容"></textarea>
  ```

  表单分组

  ```html
  <!--legend描述 fieldset块级元素-->
  <fieldset>
  	<legend>个人信息</legend>
      姓名：<input type="text" name="name" placeholder="请输入您的姓名" maxlength="5" minlength="2" ><br>
      年龄：<input type="number" name="age" placeholder="0" value="10" min="0" max="100" step="10"><br>
  </fieldset>
  ```

  outline外边框

  ```html
  input{
      outline: color style width;
  }
  ```





### 第十章       定 位

  1、position 的特点

> ​    定位的元素会原地飘起来，飘的比浮动的元素更高
>
> ​    后飘起的元素会遮盖先飘起来的元素，
>
> ​    层级相同，谁写在后面谁被遮盖
>
> ​     定位的top和left值相对于内容区域+padding的左上角定位，不能改
>
> ​     如果祖先素没有设置相对定位，绝对定位就会去找浏览器。
>
> ​    fixed相对于浏览器定位。
>
> ​    hover只能选中下边的兄弟及兄弟的子元素。无法选中上边的兄弟和祖先元素

  2.定位样式的作用：

​      完成页面中不随内容滚动的固定区域，鼠标悬停的出现的导航栏

3.定位有三个值：

> ​     position：relative；相对定位
>
> ​     position：absolute；绝对定位
>
> ​    position：fixed；窗口固定定位

4.后定位的元素比先定位的元素飘的更高，如何让先定位的元素显示呢：

​        z-index属性

```css
div{
    position：absolute；
    z-index：999     /*z-index设置定位元素的层级。只能设置一个整数值，整数包括正整数和负整数*
}
```

我们给第二个元素设置了一个层级，层级的值为1，这时他飘到了第一个元素上面，那如果我们给第一个元素也设置一个层级1会怎样呢？第二个元素设置的层级为1的时候，他又出现在了第二个元素的上方。我给了他们两个同一个层级，为什么还是不会出现在同一行呢？因为在刚才我们没有个这两个元素设置层级的时候他们的z-index都是0。而层级相同就会按元素书写的顺序决定谁在前谁在后。



### 第十一章  表格及表格布局

  1.表单元素（table）：表单就是excell表格，表单元素就是用html的方式在网页里创建表格

​    表单元素的写法：

```html
<table>
      <!--这就是一个表单元素,表单元素比较特殊，他的display值为table-->
</table>
```

​    2.表单里面的行和列：行（tr），列（td）

```html
<table>
   <!--在w3c看来先有行再有列-->
    <tr><!--tr里的t就是table，r就是row(行)， tr连起来就是表格的行-->
    	<td>1</td><!--在表格里面生成一个列，一般情况下每个td元素里的列要一样-->
        <td>26期的小仙女</td>
        <td>CE</td>
    </tr>
    <tr>
        <td>2</td>
    	<td>26期的小仙女</td>
        <td>大宝贝</td>
    </tr>
    <tr>
        <td>3</td>
        <td>26期的小仙女</td>
    	<td>与你</td>
    </tr>
</table>
```

可以发现行和列，列和列之间有一个间隙，去除间隙用border-collapse属性collapse（塌陷）

```css
/*border-collapse属性值能设置给table元素 设置给tr和td元素无效*/
table{
    border-collapse: 
        separate /*有间隙*/
        collapse /*没有间隙*/
        ;
}
```

同时如果需要改变文字在表格中的对齐顺序，同样适用text-align属性：left，center，right

3.表格里面的表头：表头（th）

```html
<table>
    <tr>
        <!--t是table h是head th就是表头的意思-->
    	<th>序列号</th>
        <th>班期</th>
        <th>昵称</th>
    </tr>
    <tr>
    	<td>1</td>
        <td>26期的小仙女</td>
        <td>CE</td>
    </tr>
    <tr>
        <td>2</td>
    	<td>26期的小仙女</td>
        <td>大宝贝</td>
    </tr>
    <tr>
        <td>3</td>
        <td>26期的小仙女</td>
    	<td>与你</td>
    </tr>
</table>
```

4.合并行货列：rowspan（行合并），colsspan（列合并）

```html
<!--合并行是竖着合并，合并列是横着合并-->
<!--合并行，行只能向下合并-->
<td rowspan="3">79期</td>
<!--合并列-->
<td colsspan="2"></td>
<!--表格在布局时如果有一列不写内容，不会空出来，而是又后天的元素补上来-->
```

5.表格的尺寸数据计算

不定死`table`元素的宽高，table的尺寸变为刚好可以容纳所有的内容。

table标签不是一个块元素，它的`display`值为`table`,它和block元素有些不一样的地方

> 1.独占一行不会和行内元素处在同一行。
>
> 2.宽高都由能内容撑开，宽度不会默认独占一行。
>
> 3.单元格的宽度由内容最多的一行决定。
>
> 4.高度有内容最多的一行的高决定。

宽高定死如何分配宽高：

  在内容宽度不够父级元素的宽度时：字符数/整行所有字符的数量 * 一行的宽度。 高度同理。

定死了宽度后，其中一列的内容非常多：在满足其他行和列能展示完内容的前提下，极大程度的占用宽度。

宽度永远不会被撑大，高度可以被撑大，设置的高度只是刚开始展示的高，高度可以被撑开

如果给每一列定宽度，本列单元格的宽度取最高。

```html
<table>
    <tr>
        <!--本列最终的宽度值是150px-->
    	<th style="width:100px;">序列号</th>
        <th>班期</th>
        <th>昵称</th>
    </tr>
    <tr>
    	<td style="width:150px">1</td>
        <td>26期的小仙女</td>
        <td>CE</td>
    </tr>
</table>
```

如果列的宽度之和大于table元素的宽度时，元素的宽度等比例缩小，公式：列的宽度/所有列的之和 * table元素设置的宽。

如果只给其中一行设置高度，其他行先被压缩到最小高度，如果继续加大其中一行的高度，高度会被撑开。

当大多数行都设置了高度，并且高度之和大于table元素的高度时，先把没有设置高度的行的高度压缩至最小，然后再给定高的设置高度。

 如果所有的行都设置了高度，而且高度之和大于table元素的高度，则会撑开table元素。 

6.border-collapse为collapse时，表格之间的边框不会合并：

```css
table{
    border-collapse:
        separate /*分离*/
        collapse /*合并*/
        ;
}
tr, td{
    border:5px solid black;/*设置之后，边框没有合并为10px*/取两个值中的最大值
}
```

那么边框是怎么显示的呢？

> 1.边框合并时，不是一边出一半，而是谁大听谁的。
>
> 2.如果宽度一样，左边框在上右边框在下。
>
> 3.边框合并时，如果两个边框的宽度一样，不是黑色的会覆盖黑色的。
>
> 4.边框宽度相同是 ->  double > dashed。

表格的区域划分：

```html
<table>
    <!--在有表祖元素的时候，打乱表祖的顺序不会打乱表格的布局-->
    <thead></thead><!--表格的头部-->
    <tbody></tbody><!--表格的中间区域-->
    <tfoot></tfoot><!--表格的底部-->
</table>
```

表格的名字：

```html
<caption>
	我是26期花名册
</caption>
```

改变表格名字的位置

```css
caption{
    caption-size:
        top /*表格的上部*/
        bottom /*表格的底部*/
        ;
}
```

文字是否换行

```css
div{
    word-break:
        normal /*使用浏览器默认的换行规则*/
        break-all /*允许在单词内换行，此时就没有单词的概念了，只有字母*/
        keep-all
        break-word
        ;
}
```

word-wrap：换行

```css
div{
    word-wrap: break-word;
}
```





### 第十二章  选择器

   一：伪类选择器

 ：checked  当选取被选中的时侯，一般用input

```css
input:checked{
    background-color: orange;
}
```

<span style="color:red">type为checkbox时有效，radio时有效，但是不能第二次选中，其他无效</span>
<input type="checkbox"> 

:hover 当鼠标进入这一区域时，适用于所有区域

```css
div:hover{
    background-color: #58a;
}
```

：link  链接未被访问时，

```css
/*没有访问过的a标签的样式*/
a:link{
    color: orange;
}
```

：active   当某个元素被激活时，input标签同样适用

```css
/*被激活时，进限于鼠标点下去未抬起来时*/
a:active{
    color: white;
}
```

`:visited `链接被访问过以后

```css
/*被访问过的链接建议设置成浅色，告诉用户这个已经访问过了*/
a:visited{
    color: #ccc;
}
```

`:focus`当链接被使用tab键选中时

```css
a:focus{
    background-color: white;
}
```

二：结构伪类选择器：nth-child

第一种情况

```html
<ul>
	<li>1</li>
	<li>2</li>
	<li>3</li>
	<li>4</li>
	<li>5</li>
	<li>6</li>
</ul>
```

```css
/*nth是第n个的意思，child是儿子的意思*/
li:nth-child(2){/*选中第一个并且是li的元素*/
    color: orange;
}
```

第二种情况

```html
<ul>
	<li>1</li>
    <p>1.1</p>
	<li>2</li>
	<li>3</li>
	<li>4</li>
	<li>5</li>
	<li>6</li>
</ul>
```

```css
li:nth-child(2){
    color: orange;/*失效*/
}
/*因为:nth-child伪类要满足两个条件:必须是li元素，而且这个li必须是第二个子元素*/
```

第三种情况

```html
<style>
    li:nth-child(2){
        color: purple;
    }
    /*2和5都变成了紫色，因为在我们没有规定父元素的情况下，页面中所有的li元素都会选中，因此这里我们不但选中了ul下排在第二个并且是li的元素，同时也选中了div下排在第二个并且是li的子元素*/
    /*如果要解决这种情况，得限制下li的选择范围*/
    ul > li:nth-child(2){
        color: purple;/*这时只有2变为了紫色*/
    }
</style>
<ul>
	<li>1</li>
	<li>2</li>
	<li>3</li>
</ul>
<div>
    <li>4</li>
	<li>5</li>
	<li>6</li>
</div>
```

`:nth-child()`伪类结构选择器里不但可以写整数，还可以写公式

```html
/*
	第一种写法：an+b / an-b 例如:2n+1 n会从0开始每次加1，因此2n+1的结果是：n为0时，2n+1=0*2+1=1；n为1时，2n+1=3
	第二种写法: an 例如: 2n 选中所有满足2的倍数的子元素
	第三种写法：Odd(符合条件的奇数子元素) / even选中所有满足条件的偶数子元素
*/
.demo > li:nth-child(an-1){
    color: purple;
}
```

`:nth-last-child()`倒数，支持公式

```html
<style>
    /*:nth-last-child()同样支持写公式*/
    li:nth-last-child(1){
        color: orange;/*3和6同时变为橘色*/
    }
    ul > li:nth-last-child(1){
        color: orange;/*3变为橘色*/
    }
</style>
<ul>
	<li>1</li>
	<li>2</li>
	<li>3</li>
</ul>
<div>
    <li>4</li>
	<li>5</li>
	<li>6</li>
</div>
```

`:nth-of-type`精准识别，什么叫精准识别呢？我们来看一下：

```html
<style>
    li:nth-of-type(2){
        color: orange;/*2和5都变为了橘色*/
    }
    ul > li:nth-of-type(2){
        color: orange;/*2变为橘色，它能找到所有子元素里的li，并且找到第二个li，不管它前面有没有其他元素*/
    }
</style>
<ul>
	<li>1</li>
    <p>1.1</p>
	<li>2</li>
	<li>3</li>
</ul>
<div>
    <li>4</li>
    <p>1.1</p>
	<li>5</li>
	<li>6</li>
</div>
```

`:nth-last-of-type`从最后找，支持公式

```html
<style>
    li:nth-last-of-type(1){
        color: orange;/*3和6都变为橘色*/
    }
    ul > li:nth-last-of-type(1){
        color: orange;/*3变为橘色*/
    }
</style>
<ul>
	<li>1</li>
	<li>2</li>
	<li>3</li>
    <p>3.1</p>
</ul>
<div>
    <li>4</li>
	<li>5</li>
	<li>6</li>
    <p>6.1</p>
</div>
```

`:first-child()`选中第一个满足条件的儿子，支持公式

```html
<style>
    li:first-child{
        color: orange;/*1和4都变为了橘色，但是会受干扰->li必须是第一个儿子*/
    }
    ul > li:first-child{
        color: orange;/*1变为了橘色，但是会受干扰->li必须是第一个儿子*/
    }
</style>
<ul>
	<li>1</li>
	<li>2</li>
	<li>3</li>
    <p>3.1</p>
</ul>
<div>
    <li>4</li>
	<li>5</li>
	<li>6</li>
    <p>6.1</p>
</div>
```

`:first-of-type`选中第一个元素，支持公式

```html
<style>
    li:first-child{
        color: orange;/*1和4都变为了橘色，不会受干扰*/
    }
    ul > li:first-child{
        color: orange;/*1变为了橘色，不会受到干扰*/
    }
</style>
<ul>
    <p>0.9</p>
	<li>1</li>
	<li>2</li>
	<li>3</li>
    <p>3.1</p>
</ul>
<div>
    <p>3.9</p>
    <li>4</li>
	<li>5</li>
	<li>6</li>
    <p>6.1</p>
</div>
```

二：属性选择器：之前我们给一个元素加样式的方式是通过class，id或者标签名来选中这个元素，除此之外我们还可以使用其他属性来选中元素给它添加样式。`[attr]`

```css
<!--首先我们可以使用属性名称来选中元素-->
<style>
    div[class]{/*选中所有有*/
        color: orange;/*1和2都变为橘色*/
    }
    [class]{/*选中所有有class属性的元素*/
        color: orange;/*1、2、3全变为橘色*/
    }
</style>
<div class="main">1</div>
<div class="container">2</div>
<p class="box">3</p>
```

`[attr=""]`属性加值选择器：

```css
<style>
    input[name="age"]{
        background-color: orange;/*type为number的背景颜色变为橘色*/
    }
    p[class="box"]{/*需要严丝合缝的相等*/
        color: orange;/*只有1变为橘色*/
    }
    p[class="box box1"]{/*空格不能少，必须完全一样*/
        color: purple;/*只有2变为橘色*/
    }
</style>
<div>
    <input type="text" name="name">
    <input type="number" name="age">
    <p class="box box1">1</p>
    <p class="box">2</p>
</div>
```

`[attr~=""]`属性中包含某值：

```css
<style>
    p[class~="content"]{
        color: orange;/*1、2、3全部变为橘色，因为他们的类名里都有content*/
    }
</style>
<div>
    <p class="content">1</p>
    <p class="content son">2</p>
    <p class="content box">3</p>
</div>
```

`[attr^=""]`属性值以谁开头

```css
<style>
    p[class^="content"]{
        color: orange;/*只有1变为橘色，其他都不是以content开头的*/
    }
</style>
<div>
    <p class="content">1</p>
    <p class="son content">2</p>
    <p class="box content">3</p>
</div>
```

`[attr$=""]`属性值以谁结尾

```css
<style>
    p[class$="son"]{
        color: orange;/*2变为橘色 因为只有2的类名是以son结尾的*/
    }
</style>
<div>
    <p class="content">1</p>
    <p class="content son">2</p>
    <p class="box content">3</p>
</div>
```

`[attr*=""]`属性值中包含某个字符

```css
<style>
    a[href*="baidu"]{
        background-color: orange;/*百度和百度网盘的颜色变为了橘色，因为只有这两个标签的href属性里有baidu*/
    }
    a[href*=".com"]{
        color: green;/*三个a标签的字体都变为了绿色，因为他们的href属性里都有.com*/
    }
</style>
<div>
    <a href="https://www.baidu.com">百度</a>
    <a href="https://pan.baidu.com">百度网盘</a>
    <a href="https://www.google.com">谷歌</a>
</div>
```

三：伪元素：`::after`和`::before`，默认都是行内元素。并且不会被爬虫和搜索引擎注意到，最重要的是js也无法选择。

`::after`在元素的最前边加上一个元素，这个伪元素里最重要的东西是`content`属性，如果没有`content`属性则这个元素报废。

> content:
>
> ​	none 不会产生伪元素
>
> ​	normal 也不会产生伪元素
>
> ​	为本内容
>
> ​	url() 外部资源如：图片，视频，音频    这个content里面不用加引号
>
> ;

```css
<style>
    div::before{
        content:"world";
    }
</style>
<div>
    hello，<!--最终显示出来的是hello world-->
</div>
```

`~`兄弟元素选择器和`+`相邻元素选择器



### 第十三章    动  画

动画的要素：

> a. 动画开始时的状态
>
> b. 动画结束时的状态
>
> c. 动画的时间
>
> d. 动画如何运行

一. 触发式动画：所谓触发式动画，需要一个触发动作来唤醒动画。

  动画样式：transition

> transition-duration：动画时间（必须是正值，不可以是负值）
>
> `transition-deley`：延迟时间
>
> `transition-property`：定义哪个属性发生动画（如果需要多个设置：transition-property:width,height,color;）可以是all
>
> `transition-timing-function`：动画速度函数
>
> ​        1.ease： 慢-快-很慢（默认）
>
> ​        2.linear:匀速
>
> ​       3.ease-in：慢-快
>
> ​       4.ease-out：快-慢
>
> ​       5.ease-in-out：慢-快-慢
>
> ​       6.cubic-bezier(n,n,n,n)（http://cubic-bezier.com -> 贝塞尔曲线）

transition的复合式样式写法：

> transition复合写法的顺序，每个属性值之间空一个空格：
>
> transition: transition-property   transition-duration    transition-timing-function;
>
> transition-delay单独写在外边。

二.  主动式动画使用animation属性。同样的animation是一个复合属性。

在做主动动画的时候，动画的帧数我们都可以自己定义，这和使用`transition`来做有点不一样，使用`transition`来做我们只能定义第一帧（默认状态）和最后一帧。那么我们怎么去自己定义动画的每一帧呢？

@keyframes属性

```css
@keyframes demo{/*demo是动画的名字，用英文随便取*/
    /*这里只是一个示例，不是说只能写0% 50% 和 100% 你可以随意写，但最小值是0%，最大值是100%*/
    0%{
        /*在这里写起始状态，不写默认是元素本身的状态，以上边的class名字为box的元素为例，默认状态就是宽300高300背景颜色橘色*/
    }
    50%{
        /*动画在运行到一半的时候是一个什么状态*/
    }
    100%{
        /*动画在运行到最后一帧的时候是一个什么样子的*/
    }
}
```

在定义了一个动画之后，我们想要看到效果，需要把这个动画的名字也就是写在`@keyframes`后的那个`name`给到一个具体的元素。

```css
.box{
    animation-name: demo;
}
```

动画时间使用 `animation-duration` 来定义，即动画持续的时间

```css
.box{
    animation-name: demo;
    animation-duration: 1s;/*动画动了起来，我们可以给他随意的秒数，*/
}
```

animation-timing-function：控制动画的速度，和触发式动画相似

animation-delay：动画延迟

在我们设置完`animation-delay`之后，动画就会在进入页面2s之后执行。但是这里有一个比较不一样的地方我们来看看：

```css
@keyframse demo{
    0%{
        width: 200px;
    }
    50%{
        width: 400px;
    }
    100%{
        width: 600px;
    }
}
.box{
    animation-name: demo;
    animation-duration: 4s;
    animation-delay: -2s;/*这样写直接从50%开始，为什么呢？因为提前执行了两秒*/负数表示提前执行
}
```

到这里animation的特性并没有学完哦~我们可以看到每次动画执行完都停留在最开始的状态，我可以让它执行完停留在最后一帧吗？完全可以：

```css
.box{
    animation-fill:
        	forwards /*动画结束后，停止在最后一帧*/
        	backwards /*默认，动画结束后，回复原状*/
        ;
}
```

使用`animation-iteration-count`定义动画的次数：可以是数字，也可以是infinity

`animation-direction`调整动画运行的方向：三个值（   alternate 正反交替运行   reverse 反向运行
  alternate-reverse 先倒着播放再正着播放）

最后我们还需要一个可以控制动画运行还是停止的属性，这个属性叫做`animation-play-state`:两个值（默认runing，暂停 paused）例

```css
.box{
    animation-play-state:
        running /*默认*/
        paused /*暂停*/
        ;
}
/*这个属性是用来让用户可以和动画产生交互的，例如：*/
.box:hover{
    animation-play-state: pasued;/*用户的鼠标进入时，动画停止*/
}
```



### 第十五章  transform（变形）

​      一.  transform的变形的属性有：translate（平移），rotate（旋转），scale（缩放），skew（扭曲）

​          1.旋转 rotate

```css
<!--这是页面的大体结构，后边设置的所有样式都是基于这个结构来的-->
<style>
    .contianer{
        width: 500px;
        height: 500px;
        margin: 50px auto;
        background-color: orange;
    }
    .top{
        width: 200px;
        height: 200px;
        background-color: purple;
    }
    .center{
        width: 200px;
        height: 200px;
        background-color: #58a;
    }
    .bottom{
        width: 100px;
        height: 100px;
        background-color: hotpink;
    }
</style>
<div class="container">
    <div class="top"></div>
    <div class="center"></div>
    <div class="bottom"></div>
</div>
```

```css
.center{
    transfrom: 
        rotate(20deg)/*rotate可以让一个元素产生旋转的效果，正值表示顺时针旋转，负值表示逆时针旋转，虽然图片发生了旋转，但是并不会影响其他元素的布局*/
        ;
}
```

默认元素是围绕着中心点来进行旋转的，那么我们有没有办法改变点的位置呢？当然可以，这里我们需要使用`transform-origin`属性:

transform-origin 变形原点，分为3d变形和2d变形，3d变形写三个值，2d变形写两个值，这里我们研究的是2d变形：

transform-origin:

​		x  可以设置的值 left center right 像素值  百分比

​		y  可以设置的值 top center bottom 像素值  百分比

;

例如： transform-origin: 

​					left top 左上角

​					center center 元素的中心点（默认值）

​					20px 20px（可以为负值） 从左上角出发向右走20px，再向下走20px的那个点

​					20% 20% （可以为负值）元素宽度的百分之二十和元素高度的百分之二十(算上padding和border)

​			;

```css
.center{
    transform-origin: left center;/*把class名称为center的元素的变形原点设置元素左边的中点后这次元素发生旋转时并不是围绕着中心点来进行旋转了，而是围绕着元素左边的中点来进行旋转*/
    transform-origin: left;/*如果只写水平方向的值，竖直方向的值为center*/
}
```

```css
.center{
    transform-origin: 20px 20px;/*这次元素围绕着从左上角出发向右20px向下20px的那个点进行旋转*/
    transform-origin: 20% 20%;/*百分比值和像素值的原理一样*/
    transfor-origin: 20px;/*水平20px竖直方向为center*/
    transform-origin: 20%;/*水平方向为20%竖直方向为center*/
}
```

用像素和百分比

`transform-origin`的值为像素值和百分比值的时候可以写成负数

```css
.center{
    transform-origin: -20px -20px;/*这时元素围绕着元素左上角向左20px，向上20px的点进行旋转，如果只写水平方向的值，竖直方向的值为center*/
    transform-origin: -20% -20%;/*原理和负像素值一样*/
}
```

`translate`属性会不户会受到`transform-origin`的影响呢？不会

```css
.center{
    transition: 1s linear;
}
.center:hover{
    transform:
        translate(300px, 300px)/*X轴和Y轴的偏移值*/
        ;
    /*写完这个效果之后发现元素是斜着过去的，如果想实现先水平移动再竖直移动或者先竖直移动再水平移动，请使用主动动画*/
```

`scale`-缩放：

```css
.center{
    transform:
        scale(1.2)/*元素被放大了，但是并不会影响其他元素的布局，只会盖上去*/
        ;
}
```

transform：scale()    scale的值可以是正数也可以是负数，包括小数，也可以是0。

​				值为0-1时缩小，值大于1的时候放大

`transform-origin`对`scale`属性同样有影响，根据变化原点的不同，缩放的位置也不一样。

下面我们来测试一下transform-origin为负值时候的样子：

```css
.center{
    transfrom-origin: -20% -20%;/*像素值同理*/
}
.center:hover{
    transform:
        scale(-2)/*这次从元素右下角出发，向左百分之20向右百分之20处变为原点，不会随着元素的放大缩小而改变位置。实操演练一下理解会更加深刻~*/
        ;
}
```

我们要学习的最后一个属性是`skew`扭曲，倾斜

> skew(x, y),skew只有两个值，没有3d的情况。
>
> x表示水平方向的扭曲程度
>
> y表示竖直方向的扭曲程度
>
> skew是一个复合样式，可以分开写：skewX(deg)和skewY(deg)

```css
.center{
      transform:
          skewX(30deg)/*水平方向扭曲30deg，里面的文字也会发生扭曲，元素不管怎样拉伸都不会影响其他元素的布局，元素的上下两条边的宽度是不变的，当拉成90deg时元素在页面中"消失"*/
          ;
}
```

```css
.center{
      transform:
          skewY(30deg)/*竖直方向扭曲30deg，里面的文字也会发生扭曲，元素不管怎样拉伸都不会影响其他元素的布局，元素的左右两条边的宽度是不变的，当拉成90deg时元素在页面中"消失"*/
          ;
}
```

扭曲样式会根据`transform-origin`的变换而产生不同。



```css
.center{
    transform: translateX(200px) translateY(200px) rorate(45deg);
}
.center{
    transform: rotate(45deg) translateX(200px) translateY(200px);
}
/*
	这两种写法的效果完全不一样，第一个先平移再旋转，第二个先旋转再平移，有什么不一样呢？
	第一种写法，刚开始元素的x轴，y轴和浏览器的x轴一致
	第二种写法，元素旋转后x轴，y轴也旋转了45deg
*/
```

总结：复合式写法，最好把rotate放在后面

如何检验代码的质量：

> 1.空间复杂度
>
> ​		代码占用的内存
>
> 2.时间复杂度
>
> ​		代码占用的cpu计算量







### 第十六章    3d变形







### 第十七章    弹 性 盒 模 型

一、 什么是弹性盒模型： 弹性盒模型是一套布局规则，里面的子元素可以根据父元素的宽高自由伸缩。 引入弹性盒布局模型的目的是提供一种更加有效的方式来对一个容器中的子元素进行排列、对齐和分配空白空间。弹性盒模型原名：flexible box

```css
<style>
    *{
        margin: 0;
        padding: 0;
    }
    .container{
        display: flex;/*开启弹性盒模型，开启之后class名字为container这个元素叫做flex container(弹性容器) 简称容器，父元素开启弹性盒模型后，里面的子元素被称为(flex item)弹性子元素*/
        width: 500px;
        height: 500px;
        margin: 50px auto;
        background-color: orange;
    }
    .container > div{
        width: 100px;
        height: 100px;
    }
    .box_one{
        background-color: purple;
    }
    .box_two{
        background-color: #58a;
    }
    .box_three{
        background-color: hotpink;
    }
</style>
<div class="container">
	<div class="box_one"></div>
    <div class="box_two"></div>
    <div class="box_three"></div>
</div>
```

开启弹性盒模型后的子项，在弹性容器里按照主轴从左往右排列。

什么是主轴呢？

> 弹性容器里有两根轴，横向的轴叫做main axis（主轴），竖直的这条轴叫做cross axis（交叉轴）。主轴从元素的左边缘到右边缘（从左往右），交叉轴从元素的上边缘到下边缘（从上往下），因此，给父元素设置为弹性容器之后，里面的子元素就会顺着主轴从左往右排列。单个元素所占的的宽度叫做main size，单个元素所占的高度叫做 cross size。

​    当一个元素开启弹性盒模型以后，如果它子元素的宽度大于父元素的宽度，也不会换行排列，而是里面子元素被压缩，弹性容器里的元素宽度永远不会超出父元素的区域。这是一个很重要的特性。

​    默认情况下，当子元素的宽度小于父元素时，我们子元素设置多宽，它就显示多宽。那么子元素的宽度大于父元素的宽度时，它该显示多少宽度呢？我们可以用下面这个公式计算一下：

>    单个元素的宽度/所有子元素的宽度之和 * 父元素的宽度

> 用上面这个公式来算一下 单个元素宽度100px；所有子元素宽度相加为600px；父元素宽500px。
>
> (100/600)*500 = 83.3px

算完宽度之后我们再来看看高度，我们都知道块级元素的高度默认是0，在这里我们注释掉盒子的高度，看看是一种什么效果：

```css
.container > div{
    width:100px;
    /*height: 100px;*/
}
```

奇怪的事情发生了，高度被注释掉以后，元素并没有消失，而是变得和父元素一样高了，因为：

> 在主轴为水平方向时，元素的宽度默认为0，高度默认和父元素保持一致。

主轴的朝向我们是可以设置改变的：通过flex-direction`属性

> flex-direction:
>
> ​	row 从左到右
>
> ​	row-reverse 从右向左
>
> ​	column 从上到下
>
> ​	column 从下到上

我们发现当值里有`reverse`的时候，写在后边的元素被排在了前边，这个特点很适合做新闻，新的新闻总是在代码里写在后边，可是我们想让他出现在第一个。当我们旋转了弹性容器后宽和高的默认情况也会发生改变。

如何让当子元素宽度大于父元素宽度的时候不被压缩：使用`flex-wrap`属性，来控制：

> flex-wrap:
>
> ​	wrap 换行
>
> ​	no-wrap 不换行

元素虽然显示了出来，但是他们之间没有空隙，挤作一团。怎么去调整他们之间的空隙呢？在这里我们不用`margin`(外边距依旧可以使用，但是不够智能)而是换做使用`justify-content`：

> justify-content绝定了弹性容器里的子元素在弹性盒子的主轴上如何进行排布
>
> justify-content:
>
> ​	flex-start 从左到右，默认
>
> ​	flex-end 从右向左排列。
>
> ​	center 居中
>
> ​	space-between 两端对齐
>
> ​	space-around 每个子元素两侧的间隔相等
>
> space-around计算公式： (父元素的宽度-子元素的宽度之和)/2*子元素个数
>
> space-between计算公式：(父元素的宽度-子元素的宽度之和)/子元素的个数减1

说完主轴之后我们来看看cross axis(交叉轴)的元素应该如何排列：

> align-items:
>
> ​	flex-start 从上到下
>
> ​	flex-end 从下到上
>
> ​	center 居中,元素的中心点对齐无视高度不一样
>
> ​	baseline 基线对齐和行内块元素不太一样，弹性盒模型只会以第一行文字的基线为准
>
> ​	stretch 默认，元素没有设置高度的时候铺满整个高度
>
> ​	auto 和stretch效果一样

接着多方几个元素，并设置换行，换完行之后发现，第二行的元素并不是紧挨着第一行的下边，而是和他之间有一个间距，这个间距使用`align-content`来控制：

> align-content:
>
> ​	stretch(默认) 子元素的高度之和不超过父元素时，计算公式：(父元素的高度-子元素的高度之和)/行数
>
> ​	center 居中显示
>
> ​	flex-start 行与行之间没有间距，并且从上向下排列
>
> ​	flex-end 行与行之间没有间距，并且从下往上排列
>
> ​	space-between 效果和主轴一样
>
> ​	space-around	效果和计算公式和主轴一样

`flex-grow`弹性增长因子

> 计算公式:元素的宽度+(父元素宽度-子元素宽度之和)*弹性增长因子/弹性增长因子之和。大于1没有意义。

 flex-shrink  弹性缩放因子

> 如果设置为0，自己不缩。
>
> 计算公式：元素1的宽度-（子元素宽度之和-父元素宽度）* (元素1的缩放因子/缩放因子之和)



### 第十八章   阿里图标和精灵图
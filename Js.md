###       第三章    DOM操作

####      1 . 什么是DOM：

​          （Document Object Model，文档对象模型）描绘了一个层次化的节点树，允许开发人员添加、移除和修改页面的某一部分，DOM的结构呈树状，所以又叫DOM树，DOM树是由很多个DOM节点组成的。

####      2 . DOM的节点分类：

>    1.元素节点（ele）：1  （常用）
>
> ​    2.属性节点（attribute）：2
>
> ​    3.文本节点（text）：3
>
> ​    4.注释节点（content）：8
>
> ​     5.DocumentFragment:文档碎片节点 11

​    DOM的节点属性：

> nodeName:元素节点的标签名，只读不能修改
>
>  nodeValue：元素节点和注释节点的内容，可读可写
>
>   nodeType：节点的类型（用于判断是什么节点），只读
>
>    attributes：元素节点的属性集合（只能修改属性值）    

####      3.   获取元素

​           1.查询DOM节点

> ​           document           获取document文档(这是一个对象)
>
> ​           document.head  获取head标签
>
> ​           document.body  获取body标签
>
> ​           document.documentElement 获取HTML标签

​           2.通过get动态获取元素

> ​           document.getElementById()       通过id获取元素(IE7以下不区分大小写,会获取name属性)
>
> ​         element.getElementsByTagName()    通过标签名获取元素（是一个类数组）
>
> ​         element.getElementsByName()          通过name属性获取元素（是一个类数组）
>
> ​          element.getElementsByClassName()	通过类名获取元素（是一个类数组）

​          3.通过querySelector静态获取元素

>   element.querySelector()			  选到指定选择器下的第一个元素(ie7及以下没有)
>
>    element.querySelectorAll()		选到指定选择器的所有元素(ie7及以下没有)（是一个类数组）

 <span style='color:red'>    总结： 动态与静态的却别：get系列是动态获取，每次使用时会重新获取，query系列是静态获取,(注意：全线浏览器兼容的，得到元素的方法，就这两个：document.getElementById() ，document.getElementsByTagName(); ) </span>

####       4、获取节点以及操作

​                  **1.基于节点树的操作（兼容所有浏览器）**

> ​           parentNode         父节点（最顶端的parentNode为document）
>
> ​           childNodes            子节点们
>
> ​           firstChild                第一个子节点
>
> ​           lastChild                 最后一个子节点
>
> ​            nextSibling            下一个兄弟节点
>
> ​            previousSibling     上一个兄弟节点

​               **2.基于<span style="color:red">元素</span>节点树的操作**

> ​            parentElement       父元素节点
>
> ​             Children                   子元素节点们
>
> ​             firstElementChild  第一个子元素节点
>
> ​              lastElementChild    最后一个子元素节点
>
> ​              nextElementSibling   下一个兄弟元素节点
>
> ​               previousElementSibling    上一个兄弟元素节点

​               **3.DOM节点的创建（增）、插入（剪切） 、删、替换**

> ​           增：document.createElement() 创建元素节点
>
> ​                     document.createDocumentFragment() 创建文档碎片
>
> ​           插入(剪切)：parentNode.appendChild(A)   在parentNode的最后面添加节点A
>
> ​                      parentNode.insertBefore(A,B)	 把节点A添加在节点B前面
>
> ​           删除：parentNode.removeChild(A)     删除节点A，删除值能保存
>
> ​                       Child.remove（A）                     删除节点A，没有返回值
>
> ​           替换：parentNode.replaceChild(A,B)  用节点A代替节点B
>
> ​         判断一个元素节点有没有子节点的方法：element.hasChildNodes()      如果有则返回true。没有则返回false        

​            <span style="color:red"> 注意： insert和append如果插入的元素存在，则剪切掉该元素原先的位置，添加到最后面，可以进行排序操作。</span>>

####    4.节点的一些属性和方法

​              **1. 元素节点常用的属性**

> innerHTML：获取元素节点的内容，可读可写（会解析标签，会覆盖原来的内容）
>
> innerText：获取元素节点的额内容，可读可写（不会被解析成标签，都被解析成文本内容）

​               **2.设置或获取标签属性**

> element.setAttribute('class','on')            设置元素节点的class属性（必须是两个参数）
>
> element.getAttribute('class')                   获取元素节点的class属性
>
> element.removeAttribute('class')           删除元素节点的class属性

​         **3.JS可以更改HTML的任何属性，方法是两种：点语法 和 setAttribute()、getAttribute()。**

```js
oImg.setAttribute("src","images/2.jpg");
等价于
oImg.src = “images/2.jpg”;
```

​         点语法：得到一个元素之后，直接打点调用它的属性名，就能对HTML相应的属性进行更改。可以获取,也可以设置。（calss特殊，因为是关键字，所以需要 .className获取）

​           **4.点语法和setAttribute（），getAttribute（）的区别**

​              1.所有自定义的属性都不能通过点语法获取和设置，只对合理（w3c的属性）属性值有效

例：

```js
<div id='box' wu='haha'></div>
const oBox=document.querySlector('#box')
alert(oBox.wu);	 //undefined，自定义的属性，不是w3c的属性，都不能用点语法
alert(oBox.getAttribute("wu"));	//haha

```

​              2.所有的行内样式,点语法.style得到的是一个样式对象。我们可以通过.style.border继续得到小样式。但是getAttribute()得到的是字符串

例：

```js
console.log(typeof oBox.style);   //object => {color：‘red’}   oBox.style.color
console.log(typeof oBox.getAttribute("style"));   //string =>"color：‘red’"  不好拿到单个属性
```

####        5.H5新增的元素节点的classList属性

​          classList属性是一个类数组，它有几个常用的方法

> add （value）：添加   为元素class增加类名，如果有就不添加，没有就添加
>
>  remove（value）：删除   为元素移出class的某个类名
>
> toggle（value）：切换    检测class属性中是否有参数字符串 有则删除 返回false,没有则添加,返回true
>
> contains（value） 返回布尔值：表示class属性中是否包含参数字符串

​            <span style="color:red">IE9及以下不兼容</span>>

####         6.H5新增了自定义属性,但是需要以data-开头

​     元素节点有一个dataset属性用来获取和设置自定义属性

​     例

```js
<div id="box" data-myName="wuwei" data-appId="123">我是div</div>
var div = document.getElementById('box');

// 获取自定义属性值
console.log(div.dataset);   // {myname: "wuwe", appid: "12"}
div.dataset.myName;        // wuwei
div.dataset.appId;         // 123

// 修改自定义属性值
div.dataset.myName = 'haha';   //haha
div.dataset.appId = '234';     // 234
```

​         <span style="color:red">IE10及以下不兼容</span>>







###  第四章：脚 本 化 CSS

####        1. 获 取 计 算 样 式 表

​          获取的值是计算后的绝对值，不是相对值，只读不可写

> ​     window.getComputedStyle(ele,null).attr               IE8以上
>
> ​       ele.currentStyle                                                       IE8及以下

​         getComputedStyle(元素,伪元素）.attr 里面传2个参数，默认第二个参数为null，也可以不传，但是要传只能传伪元素：before或者after，在获取attr属性的时候需要用驼峰命名法或者用中括号—（使用getComputedStyle获取的值都带单位px，）

例

```js
//驼峰命名
getComputedStyle(oDiv).backgroundColor;
oDiv.currentStyle.backgroundColor;
//中括号
getComputedStyle(oDiv)['background-color'];
oDiv.currentStyle['background-color'];

```

####         2.快速获得元素的尺寸和位置

​         获取元素的显示尺寸(获取的是数字类型的值)

> ele.offsetWidth : width+左右padding+左右border    自己盒子的宽度，与别的无关-全线兼容
>
> ele.offsetHeight: height+上下padding+上下border   自己盒子的高度，与别的无关-全线兼容
>
> ele.offsetLeft:   水平距离	(常用)->就是这个元素左边框外，到自己的offsetParent对象的左边框内的距离
>
> ele.offsetTop:    竖直距离	(常用)->就是这个元素边框，到自己的offsetParent对象的边框
>
> ele.clientWidth:  width+左右padding	(常用)
>
> ele.clientHeight:  height+上下padding	(常用)

​       offsetLeft  ：offsetParent就是自己祖先元素中，离自己最近的已经定位的元素，如果自己的祖先元素中，没有任何盒子进行了定位，那么offsetParent对象就是body           

​       clientWidth和clientHeight

clientWidth就是自己的width+padding的值。 也就是说，比offsetWidth少了border。

如果盒子没有高度，用文字撑的，**IE6 clientHeight是0，其他浏览器都是数值**。

####        3.获取元素有定位属性的父级

​                   ele.offsetParent:如果都没有定位，则父级body

> 封装getElementPosition函数,获取元素相对于文档的坐标

```js
function getElePos(dom){  // 获取元素相对于文档的坐标
    var x = dom.offsetLeft;
    var y = dom.offsetTop;
    var parent = dom.offsetParent;

    while(parent !== null){
        x += parent.offsetLeft;
        y += parent.offsetTop;
        parent = parent.offsetParent;
    } 
    return {
        x: x,
        y: y
    }
}
```

####     4.获取元素的滚动值

​                1.获取滚动元素的宽高

​                         当元素实际内容超过设置的内容时

> ​                 dom.scrollWidth  :元素实际内容的width
>
> ​                  dom.scrollHeight: 元素实际内容的heigh

​                    2.获取元素的滚动距离（数字类型的值）

> ​             dom.scrollTop:滚动的竖直距离
>
> ​             dom.scrollLeft:滚动的水平距离

​                    3.获取滚动条的页面滚动距离IE8以上

> ​             window.pageXOffset
>
> ​             window.pageYOffset
>
> ​             document.documentElement.scrollLeft  IE7,8
>
> ​             document.documentElement.scrollTop   IE7,8 

####       5.获得浏览器窗口的尺寸

​                    **IE8及其以上**

> ​          window.innerWidth     窗口的宽度(包含滚动条)
>
> ​           window.innerHeight    窗口的高度(包含滚动条)

#####                         IE8及其以下

> ​             document.documentElement.clientWidth	标准模式下
> ​             document.documentElement.clientHeight 
>
> ​             (在Chrome,Firefox,IE7,IE8不包含滚动条,在IE8以上包含滚动条)
>
> 
>
> ​             document.body.clientWidth			怪异模式下
> ​             document.body.clientWidth

####        6.  设置滚动条的滚动距离

浏览器页面滚动

> ​           window.scrollTo(x,y)		让滚动条滚动到指定位置
>
> ​           window.scrollBy(x,y)		让滚动条滚动指定距离

页面元素滚动

> ele.scrollTo(x,y)           
>
> ele.scrollBy(x,y)

例：

```js
const box=document.querySelector('.box'),
             op=document.querySelector('p'),
             btn1=document.querySelector('.one'),
             btn2=document.querySelector('.two');
             let timer=0;
            模仿懒加载
             btn1.onclick=function(){
                timer=setInterval(function(){
                    box.scrollBy(0,100)  
                    let scrollmove=box.scrollHeight-box.scrollTop-box.clientHeight
                if(scrollmove<200){
                    op.innerHTML+='我要学习 我要学习 我要学习  我要学习'
                }   
                 },1000)  
               
             }
             btn2.onclick=function(){
                 clearInterval(timer)
             }   

```



### 第 五 章   作用域 

####     一.作 用 域

作用域分2类：全局作用域和局部作用域（也称函数作用域),函数作用域能封闭住作用的区域：

1、函数作用域：一个变量如果定义在了一个function里面，那么这个变量就是一个局部变量，只在这个function里面有定义。出了这个function，就如同没有定义过一样，在外面访问不到此变量。

例：

```js
function fn(){
        var a=3;                 //在函数内部定义变量a
        console.log(a)         
    }
    fn();                       //此时执行该函数 a的值为3
    console,log(a)              //结果报错，因为a在全局中没有定义
```

2、全局作用域：如果一个变量，没有定义在任何的function（函数作用域）中，那么它将在全部程序范围内都有定义：就是你在js的任何位置都能够使用它.

例：

```js
var a=3                 //在全局定义变量a
function fn(){
        console.log(a)         
    }
    fn();                       //此时执行该函数 a的值为3，
    console,log(a)              //3
```

**总 结：**

<!--定义在function里面的变量，叫做局部变量，只在function里面有定义，出了function没有定义的。定义在全局范围内的，没写在任何function里面的，叫做全局变量，全局都都认识。-->

#### 二：作用域链：

###### 当遇到一个变量时，js引擎会从当前作用域逐层往外找，直到找到离它最近的第一个标识的时候停止

例： 

```js
var a=2
function fn(){
      var b=3
    function foo(){
        console.log(b)                //3  先在自己作用域找，找不到，一次往外层找，
        console.log(a)                //2  先在自己作用域找，找不到，一次往外层找，
    }
    foo()
}
fn()
```

  多层嵌套时，如果有同名的变量，则会发生“遮蔽效应”

例：

```js
var a=5
function foo(){
  var a=8
  console.log(a)                 //此时结果为8
}
foo()                    
```

作用域链：一个变量在使用的时候会先在当前的作用域中找是否被定义，如果没有，会逐层往外面找，直到找到全局作用域中，如果仍然找不到就会报错

例：

```js
var a=1,b=2
function outer(){
    var a=3
    function inner(){
        var b=4
        console.log(a)     //3 先在当前找，没有就逐往上找，找到了就停止
        console.log(b)     //4
    }
    inner()
}
outer()
console.log(a)     //1  函数作用域中的变量和值执行完就销毁了，全局作用域中访问不到
console.log(b)     //2 函数作用域中的变量和值执行完就销毁了，全局作用域中访问不到

```

如果在函数中直接给变量赋值，不写var ，js引擎就会直接帮你在全局中定义一个var

例：

```js
function a(){
 a=3
 console.log(a)
}
//console.log(a)   //此时会报错，因为函数没有执行，所有没有在全局中定义变量a
a()              //结果为3
console.log(a)   //结果为3，放到后面就不会报错了，执行完函数相当于在全局中定义了a，并且给a赋值为3，
```

函数的参数，会默认是这个函数的局部变量，不是全局变量

例：

```js
function fn(a,b,c){
    a=1,b=2,c=3
    console.log(a,b,c)
}
fn()                  //1，2，3
console.log(a,b,c)   //报错 全局中没有找到变量a，b，c
```

累加，重复调用函数的时候，不会重置(当变量定义在当前作用域外的时候，重复调用函数，值不会重置，当变量定义在函数内部的时候，会重置)

例：

```js
var a=3
function foo(){
    a++
    console.log(a)
}
foo();//4
foo();//5
foo();//6

```

```js

function foo(){
    var a=3
    a++
    console.log(a)
}
foo();//4
foo();//4
foo();//4
```

函数里面定义函数也有作用域，离开当前函数执行区间，就会报错，

例：

```js
function outer(){
    function inner(){
        console.log('hanlu')
    }
   inner()
}
outer() //正常输出结果

function outer(){
    function inner(){
        console.log('hanlu')
    }
}
  outer()      //函数
  inner()      //报错
```

#### 三、return、冒泡，递归、闭包

**return 作用**：返回值，当函数执行遇到return时，第一步是返回一个值，第二步是终止return后面函数语句执行,

例：

```js
function foo(){
    a=1
    return a
    console.log(111)
}
 foo()     //后面111不会打印出来
console.log(foo())// 1
```

<!--注意：return只能返回值，不能返回变量，所以在全局中是不能访问函数里面的变量-->

简单冒泡案例：

```js
//从小到大
var  arr_a=[3,1,4,2,5]
function maopao(arr){
   for(i=0,length=arr.length;i<length-1;i++){
            for(j=0;j<length-1-i;j++){    //length-1-i是在i层中j代表的是比较次数
                var little=0;             //定义一个信号量
                if(arr[j]>arr[j+1]){
                    little=arr[j]
                    arr[j]=arr[j+1]       //交换位置
                    arr[j+1]=little
                }
            }
         }
    console.log(arr)   //结果为[1，2，3，4，5]
}
maopao(arr_a)


//从大到小
var  arr_a=[3,1,4,2,5]
function maopao(arr){
   for(i=0,length=arr.length;i<length-1;i++){
            for(j=0;j<length-1-i;j++){    //length-1-i是在i层中j代表的是比较次数
                var little=0;             //定义一个信号量
                if(arr[j]<arr[j+1]){
                    little=arr[j]
                    arr[j]=arr[j+1]       //交换位置
                    arr[j+1]=little
                }
            }
         }
    console.log(arr)   //结果为[1，2，3，4，5]
}
maopao(arr_a)

```

递归案例：

```js
//数组递归调用
var arr_b=[3,4,5,1,2,[7,6,[9,8]]]
function digui(arr){
    for(var i=0,length=arr.length;i<length;i++){
        if(typeof arr[i]!=='object') console.log(arr[i])   //判断arr[i]的值的类型
        else{
            digui(arr[i])                                  //递归核心语句
        }
    }
    console.log(arr)
}
digui(arr_b)
//对象递归调用
var obj_a={nikname:'tony',age:18,hobbits:{eat:'rice',play:'basketball',},color:['red','yellow','pink']}
        function digui(obj){
            for(var key in obj){
                if(typeof obj[key]!=='object'){
                    console.log(obj[key])
                }else{
                    digui(obj[key])  
                }
            }
        }
        digui(obj_a)             //结果是 tony,18,rice,basketball,red,yellow,pink
```



闭包形成的必要条件：函数A内部嵌套函数B，函数A要返回函数B，并且在外部环境中执行函数B，函数B中用到函数A里面的变量值（**点击事件除外**）

例：

```js
function outer(){
    var a=33
    function inner(){
        console.log(a)
    }
    return inner
}
var inn=outer()             //形成了闭包，会把函数A的作用域一起保留住，满足两个条件：1、返回一个函数，2 在外部执行函数B需要用到函数A变量的值
inn()                      //33
```

一个函数可以把它自己内部的语句，和自己声明时所处的作用域一起封装成了一个密闭环境，我们称为“闭包” （Closures）。

每个函数都是闭包，每个函数天生都能够记忆自己定义时所处的作用域环境，但是，我们必须将这个函数，挪到别的作用域，才能更好的观察闭包。这样才能实验它有没有把作用域给“记住”。 

例：

```js
function outer(){
    var a=0
    function inner(){
        a++
        console.log(a)
    }
    return inner
}
var inn=outer()                   //形成闭包，用一个变量接收此函数的作用域环境，不断调用时，此作用域环境变量的值会不断变化
var inn2=outer()                  //用新的变量接收此函数调用时，又重新开始获取变量                 
inn()                //1
inn()                //2
inn()                //3
inn2()               //1
inn2()               //2
```

终极面试题：

```js
function fun(n, o) {
            console.log(o);
            return {
                fn: function (m) {
                    return fun(m, n);//传了m和n两个实参，1 1 fun(1,1)
                }
            };
        };
        var foo = fun(1)            //形成闭包，初始变量n的值为1，o为undefined
        foo.fn(1);    //1，到闭包找，他没有操作闭包里面的变量，所以执行完就销毁了，不改变闭包例变量的值
        foo.fn(2);    //1,继续到之前闭包找，他没有操作闭包里面的变量，所以执行完就销毁了，不改变闭包例变量的值
        foo.fn(3);    //1,继续到之前闭包找，他没有操作闭包里面的变量，所以执行完就销毁了，不改变闭包例变量的值

//另外一种执行：
     var result=fun(1).fn(2).fn(3).fn(4).fn(5)     //undefined,1,2,3,4
//也就相当于
     var result=fun(1).fn(2)             //每次都形成了闭包，都在之前闭包基础上操作
     var result2=result.fn(3)
     var result3=result2.fn(4)
     var result4=result3.fn(4)

```

总结：闭包需要返回函数，需要用到上层函数的变量，全局中调用需要有变量接收，才能形成闭包。

闭包作用：可以在全局中调用函数内部的变量，可以使其函数执行完不被销毁。







### 第 六 章  ：  对  象

#### 一.Object类型

**什么是对象?**

对象是由一对或者多对属性名和属性值组成的，我们把属性名叫做键名，属性值叫做键值，所以对象也是由很多对键值组成的;

对象是引用数据类型，操作对象时实际是在操作对象的内存地址

对象的键名是字符串类型的，键值可以是任意数据类型

对象的组成：键名和键值

例：

```js
var obj={
     nickname:'小明',
     age:18,,
     sex:'男',
}
```



**二：如何创建对象**

​    创建一个对象，有两种方法，第一种比较简单，叫做字面量；第二种是用new Object()。

​    

##### 1.1 字面量的创建方式 

plainObject   对象字面量/ 对象直接量

##### 对象的属性 的可以为以下特殊形式

1. 特殊字符
2. 数字
3. 可以有空格
4. 关键字、保留字,



符合标识符规则的属性，可以使用点语法来访问属性了，也可以使用方括号：

例：

```js
var obj = {
	name : "考拉"
} 
console.log(obj.name)
console.log(obj["name"]);
```

特殊形式的属性，必须要加上引号，检索属性的时候，必须用方括号：

```js
var obj = {
    "24&" : "哈哈",
    "all name" : "呵呵",
    "++%%%" : "嘻嘻",
    "var" : "么么哒",
    "function" : "嘿嘿"
} 

console.log(obj["24&"]);
console.log(obj["all name"]);
console.log(obj["++%%%"]);
console.log(obj["var"]);
console.log(obj["function"]);
```

对象的属性的访问，点语法是有局限的，它不能访问上面的特殊的那些情况。也不能访问以变量保存的key  例：

```js
var obj = {
    name : "考拉",
    age : 18,
    sex : "男",
    "study score" : 100
}

//console.log(obj."study score");    //错误的
console.log(obj["study score"]);	 //正确的
console.log(obj["a" + "ge"]);		 //正确的
var a = "sex";
console.log(obj[a]);			     //正确的
```

如果属性不是一个字符串会被转成字符串  例：

```js
var obj = {};
var a = {key:'a'};
var b = {key:'b'};
obj[a] = 123;
obj[b] = 345;
console.log(obj[a]);     //345
```

这里变量a,b都是对象,转换为字符串都是`[object Object]`所以这里obj只有一个属性先设置为123,后修改为345



##### 1.2 new 操作符创建对象

new Object()    构造函数创建方法

##### 构造函数创建方法有两种：1 是系统自带的构造函数 new Object（），2 是自定义的  遵循打驼峰式命名规则（ 例：Person   TheFirstName）

例：

```js
var obj = new Object();	//这是一个空对象，里面没有任何属性
obj.name = "wuwei";
obj.age = 18;
obj.sex = "男";

console.log(obj);	
console.log(obj.age);	
console.log(typeof obj);
```

new是一个运算符，你没有看错，和+-*/一样是一个运算符。表示新创建一个对象。一会儿我们学习构造函数。Object()大写字母O，这是一个系统内置的构造函数，

上面两种方式创建出来的对象，是相同的。字面量的方式直观、简单、并且有“封装”的感觉。所以我们鼓励大家用字面量来创建对象



##### 1.3、对象的属性值

对象属性值，可以是任何东西。比如数字、字符串、布尔值、正则表达式、对象、数组、函数……

##### 1.4、对象的方法

当一个对象的属性的值，是一个函数，那么这个函数我们就称为对象的“方法”(method)。

对象的方法的哲学，就是操作自己的属性。如果一个对象的方法，不操作自己的属性，那干嘛还要是方法呢？

##### 1.5、对象特点

对象的属性名是字符串类型的，当属性名不是字符串时，会把属性名隐式转换成字符串类型，调用toString()方法
对象的属性名不能重复

##### 1.6、 对象的常用操作

增加	obj.height = ‘1.8m’
删除	delete obj.name
改变	obj.name =‘xuanwu’
查看	obj.age

##### 1.7 对象操作属性名的两种方式

点操作

```js
obj.name 
```

[]操作

```js
obj[“name”] 	    //  obj.name
obj[name]	       //obj里面是一个变量，不是对象属性名称，所以是undefined
```

##### 1.8 对象的遍历

for-in循环   作用：遍历对象

例：

```js
var obj = {
    name: "wuwei",
    age:18,
    sex: "男"
}
for(var key in obj){
    console.log(key);             //name,age,sex
    console.log(obj.key);         //undefined,对象调用变量必须用方括号，打点无法调用,正确写法obj[key]
}
```

####  二、认识构造函数

构造函数内部原理,构造函数必须加new操作符,本来他只是一个普通的函数,加new就能产生构造函数的功能,构造函数的功能就是创建对象

  一旦使用new操作符,函数内部将会隐式执行三步

1. 隐式的创建一个对象,var this = {}

2. 执行代码

3. 返回this对象

   ```js
   function Person(name,age){
       // var this = {}
       this.name = name;
       this.age = age;
       this.sex = "男";
       this.say = function(){
           console.log(this.name);
       }
       // return this
   }
   var student = new Person("wuwei",18)
   ```

#### 三、包 装 类

#### 1. 数字 字符串 布尔值的包装类

基础数据类型是不能有属性和方法的大家知道吧,属性和方法只有对象有,是对象特有的,像Function,Object,Array 都是对象,原始值不能算到对象里面的,他只是一个值,作为一个独立的个体存在

数字都是原始值对吗,不对,数字分两种,只用原始值数字才是原始值

```js
var num = 123;            // 这是原始值数字
var num2 = new Number(123); // 这也是数字,这很明显是构造函数,然后new出来的对象,
console.log(num2);  // Number {123} 返回对象形式的123
```

一旦变成对象,这家伙就飞了,可以有属性可以有方法

```js
num2.name = "wuwei";
```



同时它还是具有原来值的特性

```js
var aa = num2 * 2;
console.log(aa);     // 246
```



字符串,布尔值完全一样

```js
var str = new String("wuwei");
var bol = new Boolean(true);
```



#### 2. undefined null 没有包装类 

所以不能像对象一样是用属性和方法

```js
undefined.name = "aa";
// 报错,报引用类型错误
```



现在明白了吧字符串,布尔值,数字有两种,原始值是没有属性和方法的,另外一种对象,是有属性和方法的



#### 3. 作用

```js
var str = "wuwei";
console.log(str.length);  //5
```

不是说原始值没有属性和方法吗,你这里的length是哪里来的 很明显是在操作属性啊

我们在看下能不能给他设置属性

```js
var str = "wuwei";
str.name = 123;

console.log(str.name);  // undefined
```



```js
var str = "wuwei";
str.name = 123;   
// 隐式的 new String(str);

console.log(str.name);  
// 再次new Sting(str);这个和上面不是一个String,这个对象上没有name
```



基于这样一个理论,

```js
var str = "wuwei";
str.length = 2;
console.log(str);
```

这个就是包装类,如果你发现原始值操作属性都是被隐式的包装成为了对象





#### 四、this 的指向

##### 1、认识this

this指向的是一个具体的对象，this默认指定的是window，我们把this指向的对象叫做函数执行的上下文对象

例:

```js
function fn(){
    console.log(this)
}
fn()                //结果为window
```



this指向两种对象：1、指向window，2，指向该函数被调用时的主体对象，谁调用指向谁**（在全局中也可以使用this，但是没什么必要）

例：

```js
var obj={
     nickname:'wuwei'
     inner:function (){
        console.log(this)
     } 
}
obj.inner()             //obj
```

this指向中a.b.c典型的指向型问题：

例

```js
var obj = {
            nickname:'tony',
            b: {
                nickname:'wuwei',
                c:function() {
                    console.log(this)
                }
            }
        }
        
 obj.b.c()                 //this指向的是obj.b这个对象
```

  this的另外一种案例 ,当一个对象里面的方法，在多个对象中出现，可以把这个方法封装到全局中，调用时让this指向调用的对象，目的提升性能

例：

```js
function some(){
     console.log(this.nickname)
}

var tony={
   nickname:'无为',
   foo:some
   } 
}
tony()              //无为
var yinshi={
   nickname:'银时',
   foo:some
   } 
}
yinshi()             //银时
var hanlu={
   nickname:'韩露',
   foo:some
   } 
}
hanlu()               //韩露
```







#####  2、绑定this的几种方法 

​      1:  call 方法：有两点特性（1、会执行函数改变this指向，2、括号里的第一个参数是this指向对象，后面才是传的实参（可以是任意类型））

​     例：

```js
var obj={
     nickname:'wuwei'
}
function fn(a,b){
console.log(a+b)                    //结果为7
console.log(this.nickname)
}
fn.call(obj,5,2)                    //结果为obj对象
```

#####    **2： apply方法:有两点特性（1、会执行函数改变this指向，2、括号里的第一个参数是this指向对象，后面才是传的实参，实参传入的必须是数组）**

例：

```js
function add(c,d){
    return this.a + this.b + c + d;
}
var s = {a:1,b:2};
console.log(add.call(s,3,4));          //结果为10
console.log(add.apply(s,[5,6]));       //结果为 14
```

3：bind方法：硬绑定，不会立即执行函数，而是生成一个新的函数，括号里的第一个参数是this指向对象，后面才是传的实参（可以使任意类型）

例：

```
var obj={
nickname:'wuwei'
}
function foo(){
console.log(this.nickname)
}
foo.bind(obj)                //不执行
var aa=foo.bind(obj)
aa()                          //结果为wuwei
```





##### 3、绑定分默认绑定、隐式绑定、显示绑定三种

   默认绑定：就是直接使用不带任何修饰的函数引用进行的调用,就是默认绑定,无法应用其他规则

例:  fn()  前面不带任何修饰和前缀。

  隐式绑定：考虑函数调用位置是否有上下文对象,或者说是否被某个对象拥有或包含**例：obj.fn() this就隐式的绑定到了obj身上**，还有一种情况（对象引用链只有上一层或者说最后一层在调用的位置中起作用）

例：

```js
function foo(){
    console.log(this.a);
}
var obj2 = {
    a: 42,
    foo: foo
}
var obj1 = {
    a: 22,
    obj2: obj2
}
obj1.obj2.foo();   // 42
```

 显示绑定：call方法和apply方法以及bind方法





##### 4、this绑定的优先级顺序：

例：

```js
function foo(){
    console.log(this);
    console.log(this.a) ;
}
var obj = {
    a: 23
}
var a = 33;
var bar = foo.bind(obj)
bar.call(window);//{a:23}/23
```

上述案例说明，绑定this，是有优先级顺序的，先用硬绑定bind绑定完，后面你无论用call还是apply都无法改变其this指向。

1、默认<隐式<显示<new操作符（最高）

5、特殊情况

被忽略的this

如果你传入null或undefined将会忽略传入的值,实际使用默认值

那么什么时候会需要用到传入null的情况呢

使用apply展开参数

例：

```js
function foo(a,b){
    console.log("a: "+ a + " ,b: " + b);
}
foo.apply(null,[2,3]);    //a:2,b:3
```

因为这里我们不需要关心this指向,那么我们用null占位最好,(**若值为null和undefined，this都指向默认window**）

####   五.   对 象 的 方 法

1.  ##### defineProperty（）：定义属性，键名之意就是给一个对象定义属性，语法为Object.defineProperty（obj，‘需要添加的属性名’，{属性值的配置}）

   ​    属性值的配置分为：

   ​                               1.value：‘属性值是什么’

   ​                               2.writeable：是否可写，默认为false

   ​                               3.ennumerable：是否可枚举（遍历），默认为false

   ​                               4.configurable：是否更改配置（相当于一把锁），默认为false（一旦关上就无法打开）

   例：

   ```js
    let obj = {
           nickname: '小明'
       }
       Object.defineProperty(obj, 'age', {
           value: 18,                                            //属性值
           writable: true,                                       //是否可写
           enumerable: true,                                     //是否可枚举
           configurable: true                                    //是否可更改配置
       })
       obj.age = 45                                 //{nickname:'小明',age:45}
         for(let key in obj){
             console.log(key)                              //nickname,age
         }
       console.log(obj)
   ```

   2. ##### 如何查看对象身上的某个属性配置:Object.getOwnpropertyDescriptor（对象，‘对象的属性’）

      ```js
       let obj = {
              nickname: '小明'
          }
       console.log(getOwnPropertyDescriptor(obj,'nickname'))  //{value: "小明", writable: true, enumerable: true, configurable: true}
      ```

      ```js
       let obj = {nickname: '小明'}
       Object.defineProperty(obj,'some',{
           value:"[1,2,3]",
           writable:true,
           enumerable:false,
           configurable:true
       })
       console.log(Object.getOwnPropertyDescriptor(obj,'some'))
        obj.some = 123
       console.log(obj)               //{nickname: '小明',some:123} writable为true，可更改                     
      //如果想要改some的属性配置
      Object.defineProperty(obj,'some',{
          enumerable:true               //可修改，变成可枚举（遍历）
      })
      console.log(obj) 
      //如果把configurable 锁关上
      Object.defineProperty(obj,'a',{
          value:'678',
          writable:true,
          enumerable:false,
          configurable:false
      })
      console.log(obj)
      //修改enumerable值
       Object.defineProperty(obj, 'a', {
              enumerable: true,
          })                                  //不能修改可枚举属性
          console.log(obj)                   //报错，不能重新定义a的属性
      //修改writable值
      Object.defineProperty(obj, 'a', {
              writable: false,
          })
          obj.a = 'hanlu'            //可以修改可写属性
          console.log(obj)          //{nickname: "小明", some: 123, a: "678"}    //修改configurable
      Object.defineProperty(obj, 'a', {
              configurable: true,
          })                                      //锁一旦被关上就无法打开
          console.log(obj) 
      
      ```

      总结：

      1. <span style="color:red"> 当（锁）configurable属性没有被关上时，可写属性（writable）和可枚举（enumberable）属性均可以修改。</span>>
      2. <span style="color:red">当（锁）configurable属性被关上时，可写属性（writable）如果之前是true则可更改为false，如果是false则无法更改成true，可枚举（enumberable）属性不可以被更改。</span>>

#####              3.查询对象身上有多少个私有属性方法：Obect.getOwnPropertyDectriptors（）；

例：

```js
let obj={name:'tony',hobbles:'dance',age:18}
console.log(Object.getOwnPropertyDescriptors(obj))  //显示obj所有私有属性的属性配置
```

#####          4.冻结一个对象方法：Object.freeze（obj），冻结以后，属性值不能修改，也不能新增属性

​      例：

```js
    let obj = {
        nickname: '小明',
        age: 18
    }
    console.log(Object.freeze(obj))               //冻结
    obj.age = 20                                  //原有属性值不能修改
    obj.sex = '男'                                 //不能新增属性
    console.log(obj)
```

#####       5.查询一个对象是否被冻结的方法：Object.isFrozen（obj），返回true或者false

例：

```js
 let obj = {
        nickname: '小明',
        age: 18
    }
 Object.freeze（obj）
console.log(Object.isFrozen（obj）)                   //true
let obj1={name:'tony'}
console.log(Object.isFrozen（obj1）)                  //false

```

  只要被冻住就无法解冻。

#####        万 物 皆 对 象！

```js
console.log(Object.isFrozen(123))
console.log(Object.isFrozen('123'))
console.log(Object.isFrozen(false)）        //全部为true，基本数据类型都是被冻住的对象
console.log(Object.isFrozen(true))
console.log(Object.isFrozen(undefined))
console.log(Object.isFrozen(null))
```

  6.密封一个对象的方法：Object.seal（obj），封闭以后，原有的属性值可以更改，但是不能添加新的属性值

```js
let obj={nickname:'小花'}
Object.seal(obj)
obj.nickname='小刚'
obj.age=18                                //密封之后添加新的属性无效
console.log(obj)                          //{nickname:'小刚'}
console.log(Object.getOwnPropertyDescriptor(obj, 'nickname'))                                          //{value: "小刚", writable: true, enumerable: true, configurable: false}
```

  总结：1.阻止对象添加新的属性，2.封闭以后，如果原来writable是可写的，那就可以更改原有属性的属性值，如果原来是不可写的，那就无法更改原有属性的属性值

7 判断一个对象是否被密封的方法：Object.isSealed(obj),返回true或false

```js
let obj={nickname:'小明'}
console.log(Object.isSealed(obj))              //false
Object.seal(obj)
console.log(Object.isSealed(obj))              //true

```

冻结和密封的区别：冻结是一旦冻住，所有属性无法更改，无法添加，原属性值也无法更改，密封是，一旦封闭，原先如果可写那就可写，不能修改增加属性。

8.判断某个对象身上是否有某个私有属性：obj.hasOwnproperty('属性名'),返回true或者fasle

```js
let obj={name:'小明'}
console.log(obj.hasOwnProperty('name'))                           //true
console.log(obj.hasOwnProperty( 'age'))                           //false
```

9.获取所有**可枚举**属性的键值对数组：Object.entries（对象名）,获得的是一个数组,数组里面的每一项就是该属性的键值对(不可枚举的无法获取)

```js
let obj={name:'小明',age:18,sex:'男'}
console.log(Object.entries(obj))  // [["name", "小明"],1: (2) ["age", 18 ["sex", "男"]] 
```

10,把键值对格式的数组转化成一个对象:Object.formEntries(),（具有浅拷贝功能），返回的是一个对象

```js
let obj={name:'小明',age:18,sex:'男'}
let obj2=Object.entries(obj)
console.log(Object.fromEntries(obj2))        //{name: "小明", age: 18, sex: "男"}
```

11. 对象里面比较重要的一个方法：Object.assign（obj1,obj2……）方法，合并多个对象，后面合并前面

    （**有就覆盖，没有就添加**， 对象里面的属性是无序的）

    ```js
    let obj={nickname:'小明',sex:'boy'}
    let obj2={nickname:"小刚"}
    let obj3={hobbles：'dance'}
    //后面覆盖前面
    let result=Object.assign(obj,obj2)  //{nickname:'小刚',sex:'boy'}  后面覆盖前面
    //合并
    let result1=Object.assign(obj,obj3)
    console.log(result1)      // {nickname: "小刚", sex: "boy", hobbles: "dance"}
    ```

    <span style="color:red">总结：如果前面对象和后面对象属性里面都有同一个属性，则后面会覆盖前面，否则就全部合并进去也是一个浅拷贝功能： 必须都是可枚举的私有属性，不能枚举的就不能拷贝（拷贝的是对象中的属性，属性值如果是引用数据类型则拷贝的是地址，改变新对象的属性值，原属性值也会改变，如果原属性值为简单数据类型，改变新对象，原对象不会改变）</span>

    ```js
    let obj={nickname:'小花',age:19，some:[1,2,3]}
    let result=Object.assign({},obj)
    console.log(result)
    result.age=20
    result.some[0]=666
    console.log(result)             //{nickname:'小花',age:19，some:[666,2,3]}
    console.log(obj)               //{nickname:'小花',age:19，some:[666,2,3]}
    ```





### 第七章： 数   组

#####  一、数组的4种创建方式

   1，字面量创建,用逗号隔开，最后一项不用写逗号

```js
var arr=[1,2,3]
```

​    2、通过构造函数创建数组

```js
var arr=new Array()                      //结果为[]
var arr1=new Array(6)                    //结果为[6*empty]  数组长度为6
console.log(arr1)
var arr2 = new Array({nickname: '小敏 }）；    //结果为[{nickname: '小敏 }]
  console.log( arr2 );
```

3、直接通过Array创建

```js
var arr=Array(10)
console.log(arr)               //结果为[10*empty]  数组长度为6
var ar1r=Array(nickname: '小敏 })
    console.log(arr1)           
```



总结：通过new Array和Array构造函数创建数组时，如果括号里面传入的是数字，则length长度值就等于该数子，如果括号里面传入不是一个数字： 传入的实参就是数组里的数据，如果是多个，传入的实参也就是数组里的数据。

保存数组变量实则保存的是数组的地址，例

```js
var a=[1,2,3]
var b=a
console.log(a===b)           //ture   比较地址是否一致
var c=[4,5,6]
var d=[4,5,6]
console.log(c===d)            //false 地址不一样，所以不相等
```

数组是引用数据类型，操作数组时实际是在操作数组的内存地址

数组用typeof arr方法检测，返回的是一个object，

判断一个对象是否为数组，可以用Array.isArray(arr)方法,如果为ture则是数组，反之则不是

#####          length属性

1. length属性表示数组的长度

2. 数组的索引从0开始

   

#### 二、数 组 的 方 法

#####             1、数组的头尾操作<span style="color:red;">push(),   pop(),   shift(),  unshift() </span>

 1、push ():尾部插入,语法： 数组.push(参数……)，在末尾开始插入，参数可以是任意数据类型，参数可以是一个或者多个，（<span style="color:red">返回的值是数组length的长度，会改变原数组</span>）

```js
var arr=[1,2,3,4]
var arr2=arr.push(5,6)
console.log(arr)        //[1,2,3,4,5,6]
console.log(arr2)       //6

```

   2、pop():尾部删除，语法：数组.pop(),从尾部删除数组最后一项，pop（）括号里面不接收参数，每次只能删除一个。（<span style="color:red">返回的是删除的值，会改变原数组</span>）

```js
var arr=[1,2,3,4]
var arr2=arr.pop()
console.log(arr)        //[1,2,3]
console.log(arr2)       //4
```

3、shift()：删除数组第一个数据，语法：数组.shift();从头部删除数组第一项，shift（）括号里面不接收参数，每次只能删除一个。（<span style="color:red">返回的是删除的值，会改变原数组</span>）

```
var arr=[1,2,3,4]
var arr2=arr.shift()
console.log(arr)        //[2,3，4]
console.log(arr2)       //1
```

4unshift():头部插入，语法：数组.unshift(参数1，参数2，……)，从数组头部开始插入，unshift（）括号里面接收参数，每次可以接收多个参数。（<span style="color:red">返回的是改变后数组length的长度，会改变原数组</span>）

```js
var arr=[1,2,3,4]
var arr2=arr.unshift(5，6，7)
console.log(arr)        //[5，6，7，1，2,3，4]
console.log(arr2)       //7
```

#####      

#####     2、数组的合并和切割   <span style="color:red;">concat（），slice（）</span>

concat():合并多个数组，语法：数组A.concat(数组B，数组C)，数组B的数据会全部被添加到数组A的后面,数据C的数据会等数组B的数据添加完再往后依次添加。（<span style="color:red">返回的是改变后的新数组，不会改变原数组</span>）     

```js
var  arr=[1,2,3,4]
var arr2=[5,,6]
var arr3=arr.concat(arr2)
console.log(arr,arr3)          //[1,2,3,4],[1,2,3,4,5,6]
```

   concat()的参数非常灵活，可以是数组变量、数组字面量、散的值也行，调用这个方法有复制原数组的功能，分两种情况：第1种，是基本数据类型，拷贝的是数组的值，**不会改变原数组**

例：

```js
var arr=[1,2,3,4]
var arr2=[]
var arr3=arr.concat(arr2)
console.log(arr,arr3,arr===arr3)   //arr3[1,2,3,4]  arr3!==arr  实现了拷贝功能
```

   第二种：如果是引用数据类型则拷贝的就是他们的地址，**会改变原数组**

```js
 var arr = [{nicename:'小明'},{nicename:' 小刚'}]
 var arr2 = []
 var arr3 = arr.concat(arr2)
  arr3[0].nicename="小花"
   console.log(arr3,arr)     //arr和arr3=》[{nicename:'小花'},{nicename:' 小刚'}]
                             //指向的是原数组里对象的同一地址，所有原数组中的对象会改变
                             //arr!==arr3
```

   concat复制的是原数组里面属性的地址，不是原数组的地址，故原数组！==新数组

```js
  var arr = [{ nicename: '小明' }, { nicename: ' 小刚' }]
  var arr2 = []
  var arr3 = arr.concat(arr2)
  arr3[1].nicename = "小花"         //  指向的是原数组里对象的同一地址，改变新数组对象的属性值，所有原数组中的对象属性值也会改变
  console.log( arr3[1]===arr[1])                //true
  console.log( arr, arr3 )   //arr和arr3=》[{ nicename: '小明' }, { nicename: ' 小刚' }]
```



slice():切割，截取方法，语法：数组A.slice[start，end),截取数组的数据从下标为start开始（包含start下标）到end截止（不包含end下标）  （<span style="color:red">返回的是截取出来的数组，不会改变原数组</span>）

```js
var arr=[1,2,3,4]
var arr2=arr.slice(0,2)
console.log(arr2,arr)            //[1,2]   [1,2,3,4]
```

数组的slice方法和concat方法也称为数组的**浅拷贝**功能，拷贝原数组的所有项，但是原数组和新数组地址不一样，改变新数组中的属性值，原数组也会改变，但是他们的地址不是指向的同一地址。

 

**3、数组也有深拷贝的功能，深拷贝拷贝的不是一个地址**

   **这个对象的JSON. stringify(obj)方法=》把一个对象序列化**

​    **JSON. parse(obj)方法，把一个被序列化了的对象，反序列化，变成对象**

```js
var obj={name:'小明'}
        var some=JSON.stringify(obj)  //把一个对象序列化
        console.log(some)            //'{name:'小明'}'  字符串
        var obj_a=JSON.parse(some)    //把一个字符串反序列化
        console.log(obj_a)            //{name:'小明'}    对象
```

深拷贝函数 deepCopy

```js
 function deepCopy(obj) {
            //如果传进来的不是对象类型的数据 直接打断函数执行
            if (typeof obj !== 'object' && typeof obj !== 'function') return '传进来的数据必须是对象';
            return JSON.parse(JSON.stringify(obj));   //先序列化再反序列化，就深度拷贝了这个对象，
        };
        var arr = [1, 2, 3, { nickname: '小明' }];
        var result = deepCopy(arr);
        result[3].nickname='小花'           //改变新数组里面某个对象属性值，原对象不变
        console.log(result,arr)  //arr=>[1, 2, 3, { nickname: '小明' }]
                                 //result=>[1, 2, 3, { nickname: '小花' }]
        console.log(result[0]===arr[0])          
```

**<span style="color:red">总结：浅拷贝，如果是基本数据类型，拷贝的是原数组里面的值，改变新数组里面的值，原数组不会改变，如果原数组的属性是对象，则拷贝的是数组里面对象的地址，改变新数组里面对象的属性值，原数组的属性值也会改变</span>**

<span style="color:blue;font-weight:bold">深拷贝:如果是基本数据类型，拷贝的是原数组里面的值，改变新数组里面的值，原数组不会改变,如果原数组里面的属性是对象，则拷贝的不是一个地址，改变新数组里的属性值，原数组属性值不会改变。</span>



##### **4、数组的splice（）多功能方法：可以插入，替换，切割**

语法:

> arr.splice(index,count[,item[,item2...])
>
> index为arr,下标
>
> count是要截取的数量(如果这项省略,代表从下标一直截取到最后)
>
> item,item2是截取完成后向数组中插入的内容
>
> （<span style="color:red">返回的是截取出来的数组，如果截取为空,则返回空数组，会改变原数组</span>）
>
> 例：截取，替换，插入

```js
var arr=[1,2,3,4,5]
var arr2=arr.splice(2,1,6,7)
console.log(arr ,arr2)    //[1,2,6,7,4,5] [3]  插入是从指定的下标开始
```

```js
var arr1=[1,2,3,4,'wuwei']
var arr2= arr1.splice(4,1,'tony')
console.log(arr1,arr2)
```

##### **5、数组的filter（）多功能方法**: 过 滤 数 据。

#####     语法：arr.filter((item,index,array)=>{}),过 滤 数 组<span style="color:red">（返回一个新数组，不会改变原数组）</span>

例：简单数据类型

```js
var arr=[1,2,3,4,5]
 var result=arr.filter((item,index)=>{
    return item>2     //筛选条件，
 })                   //一定要return ，不然返回的新数组，里面没有值，需要我们去return，
 console.log(result)  //返回一个新数组[3,4,5]
```

  引用数据类型

```js
var arr=[{nickname:'小花'},{nickname:"小明"}]
var result=arr.filter(item=> item.nickname==="小花")
console.log(result)                              //{nickname:'小花'}
```

**6、数组的every（）方法**: 筛选条件下判断是否全部满足，满足则返回ture，否则返回false

##### 语法：arr.every((item,index,array)=>{}),判断是否全部满足<span style="color:red">（返回ture或者false，不会改变原数组）</span>

例：

```js
var arr=[1,2,3,4,5,6]
var result=arr.every(item=> item>2)
console.log(result)                       //结果为false
```

##### 7、数组的fill（）方法：填充，

##### 语法：arr.fill(vaule,start,end)   start不写默认是0<span style="color:red">（返回新数组，会改变原数组）</span>

value为填充的值，start和end，是从下标开始到结束（[）左开右闭）

例：

```js
var arr=new Array(7)
var arr2=arr.fill(1)
console.log(arr2)                  //结果为[1,1,1,1,1,1,1]
var arr3=arr.fill(1,0,5)
console.log(arr,arr3)              //结果为[1,1,1,1,1,,]
```

##### 8、数组的copywithin（）方法：数组里面复制替换

语法：arr.copywithin（target,start,end）,target表示的从下标为几开始替换，start和end表示替换的内容是从下标几-下标几（包含开始，不包含结束）<span style="color:red">（返回新数组，会改变原数组）</span>

例：

```js
var arr=[1,2,3,4,5,6]
var arr2=arr.copywithin(1,3,5)
console.log(arr,arr2)     //[1,4,5,4,5,6]
```

##### 9、在数组里面找数据的方法：find（），findIndex（），indexof（），lastIndexof（），includes（），some（），join（）

find（）：语法： arr.find( (item, index, array) => { return } )（返回的是找到的那一项，如果没找到返回undefined，有惰性，找到一个以后就不会再往后找，不会改变原数组）

例

```js
 var arr = [1,2,3,4, 4,{ nickname: '旱麓',age: 123 }, { nickname: '旱麓',age:124 }];
    //这个数组里边有没有大于等于2的值
    var result = arr.find( item => item === 4  );
    console.log(result);                            //4

    var hanlus = arr.find( item => item.nickname === '旱麓' );  //判断条件
      console.log(hanlus);                           //{ nickname: '旱麓',age: 123 },找到第一个就不找了
```

**findIndex（）**语法:arr.find( (item, index, array) => { return } ) （找到之后返回下标，找不到返回-1）

例：

```js
var arr = [4, 1,2,3,4, 4,{ nickname: '旱麓',age: 123 }, { nickname: '旱麓',age:124 }];
    console.log( arr.findIndex( item => item === 5 ) );    //找不到返回-1
```

**indexOf（）**，语法：indexOf（）（value，start，end），value：找谁，start和end从下标几开始找到下标几结束（不包含结束下标），只能找简单数据类型 返回找到的这个值的索引,（从左往右找）

**lastIndexOf（）**;语法：lastIndexOf（value，start，end），value：找谁，start和end从下标几开始找到下标几结束（不包含结束下标），只能找简单数据类型 返回找到的这个值的索引（从右往左找）

例：

```js
 var arr = [1,2,3,4,5,2,3,4,5, { nickname: '旱麓',age: 123 }];
    console.log( arr.indexOf(2, -4) );//-1，从倒数第四位开始找，从左往右
    //lastIndexOf( value, 从下标几开始找) 返回找到的这个值的索引
    console.log( arr.lastIndexOf(1, 0) );//0
```

**includes（）**，语法：arr.includes(value, 起始下标)，返回true或者false

例：

```js
 var arr = [4, 1,2,3,4, 4,{ nickname: '旱麓',age: 123 }, { nickname: '旱麓',age:124 }];
 console.log( arr.includes(3, 7) )   //false
```

**some（）**;语法：arr.some( (item, index, array) => {} )，检测数据中是否有某一项

```js
 var arr = [1,2,3,4,5,2,3,4,5, { nickname: '旱麓',age: 123 }];
console.log( arr.some( item => item === 10 ) )      //false
```

**join（）**，语法：arr.join（）,括号里面可以传标点符号，会把数组里边的每一项都转化成字符串然后拼接成一个字符串

例：

```js
var arr=[1,2,3,4,{name:'wuwei'}]
var arr2=arr.join('&')
console.log(arr,arr2)         //"1&2&3&4&[object Object]"
```

##### 10、数组的reduce（）和reduceright（）

##### reduce（）：语法：arr.reduce( (acc,item, index, array) => {return} ),acc为数组的第一项，可以实现累加或者累乘，reduce里面可以传一个参数，那个参数默认是acc第一次执行的值，（执行是从左往右）（不改变原数组）

```js
var arr=[1,2,3,4]
var result=arr.reduce((acc,item)=>{
    return acc+item
})
console.log(result)                     //10
console.log(arr.reduce((acc,item)=>{ 
    return acc+item                       //acc第一次值默认为10
}),10)                                   //20
```



##### reduceRight语法：arr.reduce( (acc,item, index, array) => {return} ),acc为数组的第一项，可以实现累加或者累乘，reduce里面可以传一个参数，那个参数默认是acc第一次执行的值，（执行是从右往左）（不改变原数组）

##### 11.数组的排序方法：sort（），reverse（）

**sort（）排序：语法  arr.sort( (a,b) => {} )  a为后一个值，b为前一个值， 如何排序取决于函数返回的结果：**

​          **1、 大于0： b排到a的前面，  等于0： 不对调位置，小于0： a会排到b的前边，2、a - b 从小到大，b-a从大到小。（直接改变原数组）****

例：

```js
var arr=[3,1,4,6]
 console.log(var arr2=arr.sort((a,b)=>{
            return b-a
        }))
                                                 //[6,4,3,1]
console.log(arr.sort((a,b)=>{
            return a-b                           //[1,3,4,6]
        }))

```



reverse（）反转，语法：arr.reverse();作用：把原来数组中的每一个数据颠倒顺序排列**（改变原数组）

例：

```js
var arr=[{name:'tong'}，1，2，{age：10}，[7,8]]
console.log(arr.reverse())
```

**总结： **

​             **会改变原数组的方法：push（），pop（），shift（），unshift（），reverse（），sort（），copywithin（），fill（），splice（），**

​              **不改变原数组的方法：reduce（），reduceRight（），join（），includes（），indexOf（），lastIndexof（），some（），find（），findIndex（），every（），filter（），slice（），concat（）**

​               <span style='color:red'>注意： 数组方法中，find（）返回的是找到数组中的那个对象</span>



##### 12、遍历数组的方法有四种：<span style="color:orange">for循环，for  in，forEach，map for of</span> 

​         1、for ……in主要用于遍历对象，数组也是对象的一种也可以遍历，但是用的不多

​         2、forEach，语法arr.forEach（（item,index,array）=>{ }） 

​              第一个参数：数组里的每一项

​              第二个参数：每一项的下标

​              第三个参数： 原数组

​           特点：

​             1.没有返回值

​             2.不能通过item来操作简单数据类型，可以操作复杂数据类型

​             3.可以通过传入的函数去改变原数组 -> 不推荐

例：

```js
 var arr=[1,2,3,4]
       arr.forEach(item => {
                item*2                   //没有返回值
        }) 
        console.log(arr)                 //[1,2,3,4]
```

  3、map，语法：arr.map（（item,index,array）=>{ return}）参数解释同上

​    特点：map方法会返回一个新的数组，数组里边的每一项需要我们自己return返回

​               map可以通过item直接操作数组里边的每一项

​               map不改变原数组而返回新数组的优点：

例

```js
 var arr_a = [1,2,3,4,5];//原始数据
    var result = arr_a.map( (item, index) => {
        return item *= 2
    } );
    console.log(result);               //[2,4,6,8,10]  新的数组  
    console.log(arr_a);                //[1,2,3,4,5]   不改变原数组
    console.log(arr_a === result);    //false  不是同一地址
```

#####     13、Array. isArray(arr)

​           作用：判断arr是不是数组

​          如果arr是数组，那么Array.isArray(arr)的结果是true

​          如果arr不是数组，那么Array.isArray(arr)的结果是false



###  第 八 章  ：字符串方法

#####  一、字符串的创建

​      1、字面量方法

​     2、通过string函数创建

  二、字符串的的包装对象,只要使用了字符串，浏览器都会创建成一个包装对象，然后进行使用，使用完立马销毁。

```js
  let str=new String('hello world')   //构造函数
  console.log(str)                   //{'hello world'}  

 let str = 'hello world'
    str.some = [1, 2, 3]               
    console.log(str, str.some)        //‘hello world’  undefined
```

​      把字符串包装对象转化为普通字符串方式：str.valueOf（）,str.toString（）

#####   二、字符串的方法

   1. charAt        语法：str.charAt(下标)，通过下标来查找字符串中的某个字符,不会改变原字符串

      ```js
      let str='hello world'
      console.log(str.charAt(4))                  //O
      ```

2.fromCharCode     语法：String.fromCharCode（num1，num2……），参数传字符编码，通过字符编码查询对应的数字或者文字，字母。<span style="color:red">(String.fromCodePoint,用途一样）（接收多个值）</span>

3.charCodeAt        语法： str.charCodeAt（下标），根据传的下标查到对对应的字符，然后显示它的字符编码是多少（只接受传一个值有效）<span style="color:red">（str.CodePointAt（下标）功能一样）</span>

例：

```js
let   str='abcd'
let result=str.charCodeAt(2)                    //根据下标查询字符编码
console.log(result)                             //99
```

4、concat    语法：str.concat（str1，str2，str3……）    把多个字符串合并成一个字符串，（返回新的字符串，不改变原来字符串）

例：

```js
let str='小明'
let str1='adc'
let result=str.concat(str1)
console.log(result)                //‘小明adc’    返回新的字符串，不改变原来字符串
```

5、字符串的查找方法（字符串里面任何字符与任何字符之间都是以控制符串连接的）

​          （返回值为ture或者false）：

​            str.endsWith（''字符串''，字符串的长度）=>判断某个字符串是不是以……结尾的

​            str.startsWith（''字符串''，开始下标）=>判断某个字符串是不是以……开始的

​            str.includes（''字符串''，起始下标）=>从起始下标开始判断某个字符串是不是包含在原字符串里面

​             str. indexOf（‘字符/字符串’，起始下标） 从左往右查，有返回下标，没有返回-1

​             str. lastIndexOf（‘字符/字符串’，起始下标）从右往左查，有返回下标，没有返回-1

例：

```js
let str="hello world"

//endsWith
console.log(str.endsWith('d',5))  //false  传的是要查询的一个字符或者字符串，后面是查询的长度，
console.log(str.endsWith('d',11)) //true

//startsWith
 console.log(str.startsWith('hello', 0))  //true 传的是查询的字符或者字符串，后面是开始下标
console.log(str.startsWith('o', 0))  //false 

//includes
 console.log(str.includes('hello', 0))    //true
console.log(str.includes('hello', 2))     //false
//indexOf
console.log(str.indexOf('hello', 2))   //-1
console.log(str.indexOf('hello', 0))   //0
//lastIndexOf
console.log(str.lastIndexOf('w', 5))    //-1
console.log(str.lastIndexOf('w', 6))  //6
```

6、match方法 语法：str.macth（‘传需要匹配的字符串’）

​     返回结果：1 匹配到的字符串 2 找到的字符串的下标  3input  原字符串

例：

```js
let reg=new RegExp('hello','gi')   //这种写法叫正则=>正则就是用来匹配字符串的
let str='hello world!Hello world!hello world!hello world!'
console.log(str.match('hello'))      //["hello", index: 0, input: "hello world!Hello world!hello world!hello world!", groups: undefined]

//matchAll
console.log( str.matchAll(reg) );//返回迭代器对象
```

*****7 replace方法   语法：str.replace（要替换的字符串，替换成什么）

例：

```js
let reg=new RegExp('hello','gi')   //这种写法叫正则=>正则就是用来匹配字符串的
let str='hello world!Hello world!hello world!hello world!'
let  result=str.replace('hello','who')//第一个替换了，后面不变
let  result1=str.replace(reg,'who')    //不分大小写，全部替换完成
```

*****8 trim（） 删除空格     语法：str.trim（）   作用是删除前边和后边的空格   

​        trimLeft（）/trimStart（） 删除字符串开始的空格

​        trimRight（）/trimEnd（）删除字符串结尾的空格

```js
let str=' hello world '
console.log(str.trim())   //'hello world'
```

9  search（） 方法   语法 str.search（正则）立面参数是传一个正则进去，返回找到查找这个字符/字符串的下标，找不到返回-1

例：

```js
let str='hello'
let reg=new RegExp('el')                       //申明正则
console.log(str.search(reg))                    // 1
```

三、<span style="color:red;font-weight:bold">字符串的ES6书写方式 : 模板字符串</span> 

 例：

```js
//普通字符串书写方式
let str='hello world'
//字符串拼接
console.log('<span>'+str+'</span>')   //<span>hello world</span>
//模板字符串书写方式
let newstr=`hello world`
console.log(`<span>${str}</span>`)     //<span>hello world</span>  变量需要用$符加花括号括起来，
```

 书写符号不是单引号或者双引号，而是反引号=>（``），在模板字符串里面有变量需要加$变量用{}括起来。=>${ 变量名}

模板字符串里面可以包含的方式有：单双引号直接包裹，不用加换行符直接进行换行

```js
 //普通字符串书写方式
    let str = 'hello \     //换行需要加转义符号才可以
             \
        \
    world'
        //字符串拼接
    console.log('<span>' + str + '</span>')
        //模板字符串书写方式
    let newstr = `hello 
                                                      //模板字符串无论还多少行都ok

    world`
    console.log(`<span>${str}</span>`)
```

​     **${ }括号里面可以写表达式：可以是自执行函数，可以使Booler值可以使foreah或者map（for循环除外）**

例：

```js
let str=[1,2,3]
console.log(`${str}`)             //返回‘1，2，3’
console.log(`hello${ture&&false}`)  //'hellofalse'
console.log(`hello${(()=>123)()}`)  //'hello 123'

```

  模板字符串嵌套模板字符串：简单案列

```js
let arr = [{
        name: "小花",
        age: 16
    }, {
        name: "小花",
        age: 16
    }]
    let table =
        `<table>
     ${  arr.map(item=> 
           ` <tr>                                   //模板字符串嵌套，获得tr，td
                    <td>${item.name}</td>            //返回字符串
                    <td>${item.age}</td>
             </tr>
             `).join('')                              //遍历完返回的是带逗号的数组，                                                       //需要用空格清除
     }
     </table>
     `
    console.log(table)
```

### 第九章  数字方法，定时器、同步与异步、日期对象

####    一. 数字方法

   **1.在js中，计算有小数的数字，结果不准确，js里面能正常比较大小的数字范围在                     [-2的53次方+1，2的53次方-1]，**

​                安全整数：Number.MAX_SAFE_INTEGER   最大安全整数

​                                   Number.MIN_SAFE_INTEGER     最小安全整数

   **2.验证一个数字是否在安全范围内：Number.isSafeInteger（num），里面传入一个数字类型，并不会把其他数据类型转化为数字**。

3. **无穷大     正无穷大和负无穷大  ：Infinity  -infinity**

​                Number.POSTIVE_Infinity               positive[积极的]

​                Number.NEGATIVE_infinity            negative[消极的]

   **4.判断一个数字是否为有穷数：Number.isFinite（num）**

5. **判断一个数字是否是一个整数：Number.isInteger（num）**

   **6. 数字的取几位小数（四舍五入）方法：num.toFixed（保留几位小数）**

​    **7.   所有类型除了undefined和null之外都可以用toString（方法）**，

```js
let  num=123
let bool=false
console.log(num.toString())                  //'123'
console.log(bool.toString())                 //'false'
```

​      **任何一个对象使用toString（）方法结果都为[object Object],那么可以改变toString（）里面的this指向（对象.toString()是js里边最厉害的判断数据类型的方法 -> 在toString内部使用了this，而这个this指向调用toString的数据）**

```js
 //封装一个查询类型方法，根据对象的toString（），改变this指向
function fn(type) {
        console.log({}.toString.call(type).slice(7, -1))           //Number
    }
    fn(123)                                          
```

##### 8.类数组和数组的区别：数据结构是一样的，但是能用的方法是不一样的。

 **如果我想遍历一个类数组->foreach这个函数在遍历的时候是对this进行遍历，那么我们可以这样玩**

```js
[].forEach.call(类数组，(item,index,array)=>{
     console.log(item, index, array)
})
```

#### 二. 定 时 器

​         **定时器分两种：**1 延时器 setTimeout（callback（回调函数），timeout（时间））  只执行一次

​                                    2.定时器 setInterval（callback（回调函数），timeout（时间））    循环执行无数次

​         **清除定时器的两种方法**：1.清除延时器，clearTimeout（传延时器序号） 2.清除定时器 clearInterval（传定时器序号）

​         回调函数：

```js
function a(f){
    f()
}
function b(){
    console.log(111)
}
a(b)                                   //函数b当做实参传递给函数a，那么就称函数b为函数a的回调函数
```

####     三. 同 步 和 异 步

   js是编译型语言，先全部代码读一遍，然后提取一些代码（变量提升->找到所有var声明和function函数声明），提取完，然后再去执行

js代码分为两类：1.同步代码，2异步代码.执行的时候，同步代码会放到同步队列里面，异步代码会放到异步代码里面，执行队列会先执行同步队列的代码按照先后顺序依次执行（代码在执行时不能插队），然后在执行异步队列里面的代码

例

let a=2

```js
   let a = 22


        for (let i = 0; i < 5; i++) {

            console.log(i)
        }
        function fn() {

            console.log(a)
        }
        fn()       //谁在前先执行谁
```

延时器setTimeout和定时器setInterval属于异步代码，（注意：在执行阶段所有定时器都已经开始计时了，谁等待的时间短就先执行谁，跟代码先后顺序没有关系）

执行同步代码 -> 把已有的执行完成之后 如果同步代码里边新加了任务，就再去执行同步代码里边的任务，直到

所有的同步代码任务都执行完成了之后 再去异步队列里边找， 同步代码不能插自己人的队，但是可以插异步代码的队

####  四、日 期 对 象

​         js里面获取日期的方式（获取的是本地电脑系统时间）

```js
let date=new Date()
console.log(date)    //Mon Apr 27 2020 18:19:17 GMT+0800 (中国标准时间)
```

​        获取日期中的年、月、日、星期几、时、分、秒

```js
let date=new Date()
let year=date.getFullYear(),                       //获取年
     month=date.getMonth(),                        //获取月 (注意月份是从0-11)所以需要+1
     day=date.getDate(),                           //获取日
     week=date.getDay(),                           //获取周几
    hour=date.getHours(),                          //获取时
    minutes=date.getMinutes(),                     //获取分
    second=date.getSeconds()                       //获取秒
let time = date.getTime();
    console.log(time);//1587737399139ms 当前日期到1970年1月1日早上00:00:00:0000
    // //如果以1970年1月1日开始的那一刻计时，可以准确的计算1979年前一亿年和后一亿年的时间
```

倒计时需要设置时间可以如下设置

```js
let date=new Date(2021,3,4)     //2021/4/4
let date2 = new Date('December 17, 2020 03:24:00');//2020/12/17
//设置年,月,日,时,分,秒
 let abc = new Date();
    console.log(abc);

    abc.setFullYear(2021);
    console.log(abc);

    abc.setMonth(2);//2月
    abc.setDate(23);//23日

    abc.setHours(10);
    abc.setMinutes(10);
    abc.setSeconds(0);
    abc.setMilliseconds(0);

    console.log(abc);                        //Tue Mar 23 2021 10:10:00 GMT+0800
    console.log( abc.toLocaleDateString() );//转化成本地常用的日期格式  2021/3/23
    console.log( abc.toTimeString() );      //时间格式


//格林威治时间
 let date = new Date();
    console.log( abc.getUTCFullYear() );//先把abc这个日期对象的时间转化为格林威治时间
    console.log( date.getUTCHours() );//对应着英国的下午两点
    console.log( abc.getUTCDate() )
```





### 第十章   事  件

#####    1.js中的事件分为三类

> 0级事件：用来和用户进行交互，0级事件叫做事件绑定=>ele.onclick=function(){}
>
> 2级事件：用来和用户进行交互 ，2级事件叫做事件监听=>写法ele.addEventListener（''事件名称''，callback，是否捕获）
>
> 3级事件：页面内容发生变动时，交互：用鼠标和键盘操作电脑

   0级事件和2级事件的主要区别是：2级事件比0级事件多一个捕获，写法也有区别

例：

```js
//0级事件写法
box.onclick=function(){}
//2级事件写法
box.addEventLietener('click',callback,true)
```

注意：在二级事件参数中，事件名称不能带on要直接写名称，第二个参数是传一个回调函数，第三个参数是true或者false，表示是否进行捕获。

2.事件对象分为鼠标事件对象和键盘事件对象2种

​     鼠标事件：左点击（click），鼠标移入（mouseenter），鼠标移出（mouseleave），右点击（contextmenu），鼠标按下（mousedown），鼠标移动（move），鼠标抬起（mouseup）

​     鼠标事件里面属性跟键盘有关的属性：altKey,ctrKey,shiftKey,metaKey等等，判断值都为true或false 

​     ele.onfocus  获得焦点

​     ele.onblur    失去焦点

​     滚轮事件：mousewheel：根据e.wheelDelta大于或者小于0来判断是往上滚还是往下滚

```js
box.onmousewheel = e => {//wheel[滚动]
        if( e.wheelDelta > 0 ){
            console.log('向下滚动')
        }else{
            console.log('向上滚动')
       }
    }
```

   



鼠标事件里面有个button事件：0 代表鼠标左键，1代表滚轮，2代表鼠标右键

例：

```js
 box.onmousedown = e => {
     e.stopPropagation();
        //把左击，右击和滑轮点击浓缩到一起 
        e.button === 0 ? console.log('左击') : ( e.button === 1 ? console.log('滚轮') : console.log('右击') );
        if( e.button === 0 ){
       console.log('左击');
   }else if( e.button === 1 ){
       console.log('滚轮');
    }else{
        console.log('右击');
     }
    };
```

​    鼠标事件里面和位置有关的：

>    1，clientX和clientY（客户端）：代表的意思是点上去的那个点距离浏览器**可视区域**左上角坐标为（0，0）的水平和竖直方向距离，不会随着浏览器高度增加，Y轴坐标往下移
>
>    2. offsetX和offsetY：表示距离元素的左上角坐标为（0，0）的水平和竖直方向距离。
>    3. pageX和pageY：表示距离整个页面左上角坐标为（0，0）的水平和竖直方向距离，<span style="color:red">包括滚动条的距离</span>
>    4. screenX和screenY：表示距离整个电脑屏幕的左上角坐标为（0，0）的水平和竖直方向距离。
>    5. 获取元素高度和宽度可以直接 offsetHeight、offsetWidth，不用window .getComputestyle()去获取

​       

 鼠标事件里面和元素有关的：  target属性=>表示谁被我交互了，

例

```js
box.onclick=function(e){
    console.log(e.target)                      //结果为box的元素 
}
```

注意：在是箭头函数的点击事件中，this指向的是父级的作用域，所以不能直接通过this调用

例

```js
box.onclick=(e)=>{
    this.style.color=`red`          //报错
    e.target.style.color=`red`      //正确写法
}
```

##### 2.js事件中的事件冒泡和事件捕获

​       1.大部分的事件中都存在冒泡和默认行为，所以我们无论何时写事件的时候都要把冒泡和默认事件阻止了，

> ​    1.阻止冒泡的方法:e.stopPropagation（）。

> ​    2.阻止默认行为的方法：e.preventDefault（）。(例如阻止页面form表单中默认刷新)
>
> ​    3.阻止默认行为的方法：return false      (例如阻止页面form表单中默认刷新)

​      所有标签都可以使用点击事件，如果是给window和document绑定事件那么只需要绑定一个就行，因为都默认绑定的目标是body，所以没必要重复绑定。

​         2.什么是事件冒泡：事件冒泡指的是当点击页面中的某个元素时，点击事件会一层一层往上传递（只和自己的父元素或者祖先元素有关），所有浏览器都有事件冒泡。

​       3什么是事件捕获：在2级事件中，捕获属性设置为true那么该点击事件就有了捕获阶段，捕获阶段是从上往下捕获，而事件冒泡与之相反。

​      **总结，当无论是事件冒泡还是事件捕获，当某一层设置了阻止冒泡或者捕获那么冒泡和捕获到该层以后就不会继续向上或者向下执行。**



##### 3.移动端的专属事件：

> 1.touchstart：手按下
>
> 2.touchmove：手移动
>
> 3.ontouchend：当触摸结束
>
> 4.touchcancel：触摸意外终止- >正在刷今日头条,突然接到了旱麓的电话,电话页面会变到最上层，覆盖了今日头条，触摸意外终止

​               TouchEvent -> 触摸事件对象

​                changedTouches和touches，他们两个完全一毛一样

​                length属性：几根手机进行了触摸 -> 可以通过判断length来看有几根手机进行了触摸

例：

```js
box.ontouchstart=function(e){
    console.log(e)  // 放手按下的那一刻
}
box.ontouchmove=function(e){
    console.log(e)  //手指在整个页面里边滑动
}
box.ontouchend=function(e){
      console.log(e)  //手指离开的那一刻
}
box.ontouchcancel=function(e){
     console.log(e)  //手指意外离开了
}
```

#####   4.事件绑定或监听多个会不会覆盖 

​           1、0级事件：事件绑定->不能重复绑定，否则会被覆盖（后面覆盖前面）

​            2、2级事件：事件监听->不能重复绑定同一个callback（回调函数）、如果绑定的不是同一个回调函数，则都执行

​          3、事件注销：

​                 0级事件：通过重新赋值为null来注销，例：box.onclick=null，

​                 2级事件：Element.removeEventListener('取消什么事件的监听', 取消哪个callback)

​     





​       

### 第十一章：ajax 技 术

   1. ##### ajax的作用：如何实现前后端交互 传输数据->通过ajax实现（用来在js里边去向后端请求数据）

      （如何安装ajax环境：

      > 1.在百度里面搜索node.js官网，打开并下载12.16.3长期支持版本
      >
      > 2.按window+r键打开cmd命令黑窗口，输入node（空格）-v和npm（空格） -v 检查node.js是否安装成功（是否显示相应的版本号）
      >
      > 3.切换下载源  在百度里面搜 淘宝镜像源（npm config set registry https://registry.npm.taobao.org）
      >
      > 4.进入ajax文件夹（文件名不能使用中文），按照shift+鼠标右键，打开黑窗口
      >
      > 5.输入 npm init -y 初始化
      >
      > 6.输入 npm i express 等待安装完成，（意思是在安装express框架）
      >
      > 7.输入 npm body-parser（安装中间件）
      >
      > 8.输入 npm i -g nodemon（比较重要）
      >
      > 8.在vscode里面打开ajax文件夹，并新建app.js文件，在命名台，输入 nodemon app.js把服务跑起来

​        （如何在app.js里面运行步骤： 

​                   1.声明一个变量ex，引入 require（’express‘）框架

​                    2.声明一个变量body-parser，引入 require（’body-parser‘）中间件

​                    3.运行声明框架app=ex（） 

​                    4.声明端口号

​                     5.app.use(express.static(''输入一个文件夹的名字”)

​          例：

```js
const express = require('express') //引入express框架
const bodyparser = require('body-parser') //引入中间件
const app = express() //主程序运行
const port = 3000 //端口
app.use(express.static('public')) //引入一个文件夹
app.listen(port, () => {
    console.log(`服务器运行在${port}端口`)
})
```



 **2.如何实现通过ajax在js里边去向后端请求数据**

```js
<script>
    //第一步实例化一个ajax对象（助理）
    const xhr=new XMLHTTPRequest（）  //用http协议请求数据（向后端请求）
    xhr.open('get','http://localhost:3000') //向后端发送请求，接收两个参数（‘请求方式’，‘向那个地址请求’）
    xhr.send()  //需要有个发送的过程，里面发送的是传给后端的数据，如果什么都不传，可以写null，也可以不写
</script>
```

​      **3.请求的方式一共有四种：**

> 1.get  查询（也叫获取）
>
> 2.post 增加
>
> 3.Delete 删除
>
> 4.put   修改

​        **4.请求HTTP：//localhost：3000，的时候返回一个html文件**

> 1.  http：//是固定的格式
> 2.  localhost 是域名（IP地址）
> 3.  3000表示端口号（80-60000）
> 4.  /wangzhang  表示的是路径（根路径或接口）

   总结:（4）整体就构成了一个URL地址，（2）  XML数据格式：发送和请求XML这种数据格式（不单单可以发送XML这种数据，任意数据类型都可以）->所有用于发送请求的函数和所有后端返回的数据都放在这样的一个对象里面。

​    **5、前后端发送数据状态监听检查**

```js
<script>
    xhr.onreadystatechange=function(){
    if(xhr.readyState===4){    //判断状态是否为4->已完成状态
        if(xhr.status>=200&&xhr.status<300||xhr.status===304){//判断是否拿回来了数据
            console.loh(xhr.responseText)      //回来了，成功拿到数据
        } else{
             console.loh(xhr.status)             //回来了，但是没有拿到数据（就可以根据状态码知道是哪里的问题）  
        }
   }
}
 </script>
```

#####       6、 readystatechange监听改变状态

​          1.readystate：准备状态，共有个值

> ​       0：未初始化，ajax对象还没有创建成功。
>
> ​       1：启动，已经调用open方法，但是还没有调用send方法。
>
> ​       2.发送，已经调用send方法，正在去后端拿数据的路上。
>
> ​       3、接收，已经接收到部分相应的数据。
>
> ​       4、接收完成，已经接收完全部相应的数据，返回回来。  **注意（4表示回来了，但并不一定说明他拿到了数据）**

​         2.status：http请求的状态码  从100到600之间，而且一定是一个整数

> ​      看到[200,300)之间的任意一个数字，都表示一切正常    (304[正常])
>
> ​       300是重定向：304[正常]=>去缓存里面拿数据，也是重定向
>
> ​       400 前端出错
>
> ​       500：后端出问题

​         3、从后端返回来的数据都存放在 responseText属性和response属性里面，官方推荐使用responseText属性

#####      7、四个发送方式的详解与区别

#####    1  get 查询（获取）：

​                    可以把要发送的数据写在send（）里面，但是这不是常用的方式，

​                    直接在请求路径里面发送数据：给路径添加参数：格式为-> 路径?属性名=属性值&&属性名=属性值……（可以发送n多个数据）  例：

```js
<script>
    //在js中
    app.get('/wanzhang', (req, res) => {
    if (req.query.wife === '石原里美') {
        res.send('成功')
    } else {
        res.send('失败')
    }
   })

     //在HTML中
    //第一步实例化一个ajax对象（助理）
    const xhr=new XMLHTTPRequest（）  //用http协议请求数据（向后端请求）
    xhr.open('get','http://localhost:3000/wangzhang?wife===石原里美') //向后端发送请求，接收两个参数（‘请求方式’，‘向那个地址请求’）
    xhr.send()  //需要有个发送的过程，里面发送的是传给后端的数据，如果什么都不传，可以写null，也可以不写
</script>
```

#####     2 、post 增加（向后端数据插入内容）请求，是在 send（）里面发送数据

​          报错 404 代表你请求的路径不存在

​         控制台里面 network的headers里面放的是请求头

​         每一个http请求都是带有相应的请求头信息，只是这里面很少是给我们开发者看的，

​          Response Hraders：后端返回数据时的请求头

​           Request Headers ：前端发送请求时的请求头

​            Request Payload：前端发送给后端的数据

​            前端发送给后端的任何数据都必须是字符串

​         （ 在请求头里面有以下部分数据

> ​        Accept：浏览器能够处理的内容类型
>
> ​        Accept-Encoding：浏览器能够处理的压缩编码
>
> ​         Accept-Language：浏览器能够处理当前设置的语言
>
> ​         Connection：和服务器的连接类型
>
> ​         Content-type：数据类型
>
> ​          host：域名
>
> ​          Origin：协议+域名

  如何设置请求头：xhr.setRequestHeader（‘键名’，‘键值’）

​    例

```js
//html页面
<script>
    let  obj={name:'hanlu'}
    const baseUrl='http://localhost:3000'
    const  xhr=new XMLHTTPRequest();
    xhr.open('post',`${baseUrl}/contact`)
    xhr.setRequestHeader('Content-Type','application/json')//设置请求头，让浏览器发送的时候以对象的形式发送
    xhr.send(JSON.stringify(obj))//把数据发送给后端，把对象序列化一下
    xhr.onreadystatechange = function () {
       if( xhr.readyState === 4 ){
             if( xhr.status >= 200 && xhr.status < 300 || xhr.status === 304 ){
                console.log(xhr.responseText);
            }
       }
    }
</script>

//js后端页面
const express = require('express') //引入express框架
const bodyparser = require('body-parser') //通过post传输需要引入中间件
const multiparty=require('multiparty')//通过post传输需要安装这个
const app = express() //主程序运行
const port = 3000 //端口
app.use(express.static('public')) //引入一个文件夹
app.use(bodyparser.json())        //通过post传输需要使用中间件
app.use(bodyparser.urlencoded({extended:false}))//通过post传输需要使用
app.listen(port, () => {
    console.log(`服务器运行在${port}端口`) //端口号监听一定要加上
})
app.post('/contact', (req, res) => {
    console.log('params:', req.params, 'body:', req.body, 'query:', req.query)
    res.send('font end')
})
```



post更多是用来传输表单数据，在用表单传输数据的时候有独有的数据格式->formdata[表单数据]

```js
  //前端代码
const form=document.querySelector('form')
     let  formdata=new FormData(form)
     const baseUrl = 'http://localhost:3000'
     const xhr = new XMLHttpRequest();
     xhr.open('post',`${baseUrl}/Formdata`)
     xhr.send(formdata)
     xhr.onreadystatechange = function() {
        if (xhr.readyState === 4) {
            if (xhr.status >= 200 && xhr.status < 300 || xhr.status === 304) {
                console.log(xhr.responseText);
            }
        }
    }
//后端代码
app.post('/contact', (req, res) => {
    const form = new Multiparty.Form()      //这部分是表单数据传输给后台，后台如何进行处理
    form.parse(req, function(err, fields, files) {
        console.log(fields)
    })
    res.send('我已接收所有表单数据')
})
```

 请求方式总结，在请求方式为post的时候，一般分2种情况，一种是json格式，一种是formdata格式

1. json格式：第一步：需要设置请求头，setRequestHeader（‘Content-Type’,‘application/json’）

​                        第二步：把传入的对象序列化xhr.send（JSON.stringify（obj））

   2.formdata格式：先把拿到的form元素，实例化一下，例： let  formdata=new FormData(form)  ，随后直接发送 send（formdata）传输就行

​    ajax里面的其他事件：

> ​          1.onload事件：当ajax返回的时候触发(相当于readystate=4)
>
> ​           2.error事件：ajax出错的时候要触发的函数
>
> ​          3.abort事件：手动终止ajax对象（场景：例如突然来电话，打断）
>
> ​          4.是否携带cookie：xhr.withCredential=true;默认为false（小甜饼，携带用户信息）

   （  onload ajax返回触发）

```js
  //只在readystate为4的时候搞事情
    const xhr = new XMLHttpRequest()
    xhr.open('get', 'http://localhost:3000/logins?some=123')
    xhr.withCredentials=ture;//携带上浏览器里边保存的cookie
    xhr.send(null)
    xhr.onload = function() {
        if (xhr.status >= 200 && xhr.status < 300 || xhr.status === 304) {
            console.log(xhr.responseText);

        }
    }
```

 （error ajax出错触发）

```js
  const xhr = new XMLHttpRequest()
    xhr.open('get', 'http://lcalhost:3000/logins?some=123')
    xhr.send(null)
    xhr.onerror = function() {
        console.log(xhr.status);
    }
```

（abort 手动打断）

```js
 const xhr = new XMLHttpRequest()
    xhr.open('get', 'http://localhost:3000/logins?some=123')
    xhr.send(null)
    xhr.onreadystatechange = function() { //一共会触发3到4次
        if (xhr.readyState === 3) {
            xhr.abort(); //手动终止了数据请求
        }
        if (xhr.readyState === 4) {
            if (xhr.status >= 200 && xhr.status < 300 || xhr.status === 304) {
                console.log(xhr.responseText); //后端返回的数据是无法在前端使用的
            }
        }
    }
```

   **（Ajax总结： ajax的流程）**

​     **1. 实例化ajax对象**

​     **2.open('做什么', '去哪里做')**

​     **3. send()**

​        **1.get -> send(null)**

​        **2.post -> （一）send(表单数据) （二）设置请求头，在请求头里边把数据格式设置为json格式，浏览器才能把 正确的数据发送给后端, send(你要发送的json数据)**

​      **xhr.onreadystatechange = function () {}监听状态变化，拿到后端返回的数据**

   3.自定义中断时间 ：3秒钟之内要是请求没有完成就不请求了-> xhr.timeout

​       ontimeout:超时，会打断ajax执行

​      ajax的特点：它是异步的，send是异步的

例：

```js
 //实例化一个ajax对象
    let num = 0;
    const xhr = new XMLHttpRequest()
    const url = 'http://localhost:3000'
    xhr.open('get', `${url}/logins?some=123`)
    xhr.send(null)
    xhr.timeout = 3000;
    xhr.onreadystatechange = function() {
        // if (xhr.readyState === 3) {
        //     xhr.abort()
        // }
        if (xhr.readyState === 4) {
            if (xhr.status >= 200 && xhr.status < 300 || xhr.status === 304) {
                num = xhr.responseText
                console.log(num)
            }
        }
    }
    xhr.ontimeout = function() {
        console.log('请求出错')
    }
    console.log(num)
```





### 第十二章.   pormise  (es6)

​     1.   **什么是promise**

​             promise是es6里面的属性，主要用途：处理异步返回值的一种解决方案，只能让我们用编写同步代码的方式去处理异步结果，并不能决定异步结果。

​    **2.promise是一个构造函数**：new promise（callback）：callback=》要处理的事情，返回一个promise对象。它本身是同步的，实例化之后会立即调用callback函数

   例：

```js
<script>
    const promise=new Promise(()=>{
        console.log(1)
        setTimeout(()=>{
            console.log('我是promise里面的settimeout')
        },1000)
    })
</script>
```

​    3.promise里面的回调函数会被传入2个实参，   这两个实参都是函数，并且是由JavaScript引擎提供的，promise（）有三种执行状态

>    1.pending：正在执行中
>
>    2.resolved： 代码执完了并且成功了
>
>    3.reject：代码执行完了同时失败了

​          

```js
let date=0;
const promise=new Promise((resolved,reject)=>{
    setTimeout(()=>{
        date=4
        if(date<4){                         
        resolved(date)      //决定了promise的状态，当代码执行成功时，走then里面的第一个回调函数，把date数据传了出去，传到了then的一个回调函数里面
    }
    else{
        reject(`错误的原因是data为${data},他不小于5`) //失败之后走then里面的第二个回调函数，把data数据传给了第二个回调函数里面
    }
    },1000) 
})
promise.then(abc=>{
    console.log(abc)              //then第一个回调函数，promise状态成功传入
},err=>{
    console.log(err)               //then第二个回调函数，Promise状态失败后传入
})
```

4. **.then用变量接收后会返回一个全新的promise对象，可以层层嵌套**

   ```js
    let some = promise.then( abc => {
   
           console.log('成功为:', abc);
           return '我是some';
   
       }, err => {//errquanpin[error] 表示错误
   
           console.log(123)
           console.log('错误为',err);
           //如果想在代码错误了之后在这里做一些补救措施
   
       } );
   
       let ggg = some.then( xyz => {
   
           console.log( '第二遍then执行了，上一个then传递过来的数据为',xyz );
           return {nickname: '小明'};
   
       }, err => {//捕获第一个then里边的代码运行错误
   
           console.log('出错了');
       } );
   
       ggg.then( data => {
           console.log('ggg这个then里边的数据为:', data)
       } );
   
      console.log(some)  //promise{<pending>}
   ```

   总结：通过马儿跑经典理解下，promise类似于马儿跑，从起点到终点，如果是第一名：奖励，不是第一名：不奖励，promise里面的代码相当于马儿正在跑，把失败或者成功的数据传出去，promise.then就是比赛结束以后还需要做的事，（promise(callback1,callback2)）

    当失败以后有两种情况：

   ​    1.第一种错误情况：结果没有达到我的预期。

   ​    2.第二种错误情况：代码本身错误了.通过try，catch也可以继续向下传递给callback2

     **5.当有两个promise对象，并且promiseB中返回的回调函数是promiseA的数据时，那么B的状态就失效了，和A的状态保持一致**

   例：
   
   ```js
   1.promise的res和rej里边可以继续传一个promise
        let p1 = new Promise( (res, rej) => {
            setTimeout( () => {
                rej( { code: -1, msg: '出错了' } )
           }, 2000 )
        } );
        //p2 1秒钟之后成功，p2两秒钟之后失败
        //a promise的res里边传的参数是 b promise，那么a的成功或者失败取决于b
        let p2 = new Promise( (res, rej) => {
            setTimeout( () => {
                res( p1 )//res表示成功
            }, 1000 )
        } )
        .then(
            data => {
              console.log(data)
           },
           err => {
               console.log(err);
           }
        );
   ```
   
   6. **promise 的catch方法：捕捉promise错误**
   
      catch可以取代.then中的第二个回调函数:如果把promise的状态定位失败,然后又没有相应的补救措施,就会抛出一个红色错误(安全的)
   
      ```js
         let p3 = new Promise( (res, rej) => {
              setTimeout( () => {
                  rej( { code: -1, msg: '用户不存在' } )
              }, 1000 )
          } )
          .then( data => { console.log(data) } )
          .catch( err => { 
              if( err.msg === '用户不存在' ){
                  alert( err.msg )
              }
          } );
      ```
   
      catch返回的依然是一个Promise对象:例
   
      ```js
       let p3 = new Promise( (res, rej) => {
              setTimeout( () => {
                  rej( { code: -1, msg: '用户不存在' } )
              }, 1000 )
          } )
          let succse=p3.then( data => { console.log(data) } )
          let fail=p3.catch( err => { 
              if( err.msg === '用户不存在' ){
                  alert( err.msg )
              }
          } );
          console.log(fail)                     //Promise{<pending>}
      ```
   
      在很多个Promise环节中，只要有任何一个环节出错，都可以用catch来捕捉错误
   
      ```js
        let p5 = new Promise( (res, rej) => {
              res( { code: -1, msg: '成功' } )
          } )
          .then( abc => {//处理第一次成功
              console.log(abc)
              // throw new Error( JSON.stringify( { code: -1, msg: '第二个错误' } ) );
              return abc
          } )
          .then( xyz => {//处理第二次成功
              throw new Error( JSON.stringify({code: -1, msg: '第三个错误'}) )
          } )
          .catch( err => {
              console.log(err)
          } );
      ```
   
      **7.Promsie.all 方法**:**把多个promise实例包装成一个新的promise**
   
      ​    语法:Promise.all（[promise1,promise2,promise3]）
   
      ```js
      const baseUrl = 'http://localhost:3000';
      
          let some = [ `${baseUrl}/log`, `${baseUrl}/vip`, `${baseUrl}/download` ].map( item => request({ url: item }) );//request为返promise的函数
          
          let result = Promise.all( some )
          .then( data => {
              console.log(data)
              //every查找所有数组项,全部为真则为true,只要有一个为假,都为false
              let jieguo = data.every( item => item === 'true' )
      
              if( jieguo ){
                  console.log('歌曲正在下载')
              }else{
                  alert( '权限不足不能下载' )
              }
      
          } )
          .catch( err => {//只要有一个promise失败了，所有的都失败了
              console.log(err)
          } );
      ```
   
      8.Promise.race:相当于赛跑,谁第一名听谁的
   
         语法:Promise.race([promise1,promise2,promise3])
   
      ```js
      
          let haras = [1000, 1200, 1300].map( (item, index) => new Promise( (res, rej) => {
              setTimeout( () => {
                  res(index + 1)
              }, item )
          } ) );
      
          Promise.race( haras )
          .then( data => {
              console.log( `第${data}匹马获得了胜利` )    //第1批匹马获得胜利
          } );
      ```
   
      **总结**:  <span style="color:red">异步Promise 是异步的， 定时器和延时器也是异步的 -> 大家都是异步的，谁先执行呢？Promise先执行  异步: 微 和 宏</span>

​              



###    第十三章： 面向对象（封装，继承，多态，原型，原型链）

​     1.最简单封装解决问题方法（工厂模式下）

```js
function createUser(nickname,age){
      const obj={
            nickname:nickname,
            age:age
        }
        return obj
    }
    const obj2=createUser('小红',3)
    const obj3=createUser("小明",5)
    console.log(obj2,obj3)   //{ nickname：小红，age：3}，{nickname：小明，age：5}
```

​      在创建对象的时候给他们添加上独特的方法，例如介绍自己的方法（introduce）   

```js
 function createStudents(nickname,age,favorColor){
      const obj={
            nickname:nickname,
            age:age,
            favorColor:favorColor,
            introduce:function(){
              //console.log(`大家好，我是${nickname},今年${age}岁了,喜欢${favorColor}`)//这里形成了闭包，为了增加性能，所以要把闭包干掉
             console.log(this)//this指向调用它的主体对象，也就是obj
             console.log(`大家好，我是${this.nickname},今年${this.age}岁了,喜欢${this.favorColor}`)
            }
        }
        return obj
    }
    const obj2=createStudents('小红',3,'red')
    obj2.introduce()
    const obj3=createStudents("小明",5,'black')
    obj3.introduce()

```

 由上可知，introduce方法被写了三次，性能不够好。

2.通过构造函数来实现

​     什么是构造函数

​       new：

​          1.创建了一个对象 ({})

​          2.将函数的this指向了这个对象

​          3.执行构造函数里边的代码

​          4.返回新对象 -> 返回new创建出来的这个对象

```js
function introduce(){
                console.log(this)
                console.log(`大家好，我是${this.nickname},今年${this.age}岁了,喜欢${this.favorColor}`)
            }
function CreateStudents(nickname,age,favorColor，introduce){
            this.nickname=nickname
            this.age=age
            this.favorColor=favorColor
            this.introduce=introduce
    }
     let obj=new CreateStudents('小红',3,'红色',introduce)
     let obj2=new CreateStudents('小刚',4,'黑色',introduce)
     let obj3=new CreateStudents('小明',5,'绿色',introduce)
     obj.introduce()      
     obj2.introduce()
     obj3.introduce()
```

同样，通过构造函数传参的方式，方法也被写了三次，性能还是不够强（ 目前，这两种方式都有一个缺点：   introduce这个方法被创建了三遍，实现相同功能的函数被写了三遍。不好！）

```js
function introduce(){
                console.log(this)
                console.log(`大家好，我是${this.nickname},今年${this.age}岁了,喜欢${this.favorColor}`)
            }
function CreateStudents(nickname,age,favorColor){
            this.nickname=nickname
            this.age=age
            this.favorColor=favorColor
    }
     let obj=new CreateStudents('小红',3,'红色')
     introduce.call(obj)                           //通过显示绑定this调用函数
```

函数是一个引用类型的数据,虽然在三个对象上边都有introduce方法，但是三个introduce属性指向了同一个函数，那么也就是说，introduce函数只有一个。（不太好，abc函数是为Students构造函数实例化出来的对象服务的）

####   3.原 型

​        1.什么是__proto__ 原型：保存着这种数据类型共有的方法（工具箱），我们可以直接调用：例如我们在使用数组的forEach方法时，其实就是在使用数组原型上的forEach方法。

​        2. 浏览器查找对象属性的规则：

​        浏览器查找对象属性的步骤：1.去对象的私有属性里边找，如果找得到就用，如果找不到就去原型上找，如果原型上也找不到，就是undefined

​       3.不同的数据类型是被不同的构造函数创建出来的：

​          差别在于，他们的共有属性(公共方法)是由不同的构造函数提供的。

   4. 创建自定义对象的原型： 箭头函数不能被当成构造函数使用.

   5. 每一个function声明的函数身上都有prototype[原型]这个属性。这个对象会成为被new出来的对象的原型__proto__

      例:

      ```js
      function CreateStudents(nickname,age,favorColor){
                  this.nickname=nickname
                  this.age=age
                  this.favorColor=favorColor
          }
      let obj=new CreateStudents('小红',3,'红色')
        console.log(obj.__proto__===CreateStudents.prototype)   //true
      
      ```

      用原型来解决上面的问题

      ```js
       function CreateStudents(nickname, age, favorColor) {
           //创造私有属性
              this.nickname = nickname
              this.age = age
              this.favorColor = favorColor
          }
      //创造公用方法
          CreateStudents.prototype = {
              // 加上是由哪个构造函数而来的
             consturtor:CreateStudents,
            introduce: function () {
              console.log(`大家好，我是${this.nickname},今年${this.age}岁了,喜欢${this.favorColor}`)
             }
          }
          const obj2 = new CreateStudents()
          console.log(obj2)
      ```

      

      上面美中不足的地方是给原型上添加个对象，没有consturtor属性，需要手动添加，然后添加的consturtor属性是可枚举的，

      但是直接在原型上添加某个方法，就没有这个问题。例：

      ```js
       CreateStudents.prototype.introduce = function () {
                  console.log(`大家好，我是${this.nickname},今年${this.age}岁了,喜欢${this.favorColor}`)
              }                          //有consturtor属性，是不可枚举的
      ```

      如何解决上述案例中给原型上面添加对象，对象里面的放法是可遍历的（for in循环可以遍历到原型，可以遍历出来所有可枚举的属性）：<span style='color:red'>通过给构造函数原型配置对象就可以解决</span>>

      ```js
         function Man(nickname, age, favorColor) {
              this.nickname = nickname
              this.age = age
              this.favorColor = favorColor
          }
         Object.defineProperties(Man.prototype,{
              introduce:{
                  value:function(){
                      console.log(`大家好，我是${this.nickname},今年${this.age}岁了,喜欢${this.favorColor}`)
                  },
                  enumerable:false,//设置成不可枚举
                  writable:true  //设置成可写的
              },
               consturtor:{
                   value:Man
              }
          })
          let obj5=new Man('小明',3,'red')
          console.log(obj5)
      ```

      ​       **动态性：可以去更改原型**

      ​            1.如果在改变原型之前已经实例化了对象，那么这个对象无法访问到新原型上的方法，

      ​            2.如果只是在原来 原型的基础上添加了一些方法，那么实例化出来的对象就能够访问新加的方法

      例：第一种情况，在原型的基础上添加一些方法，

      function Man(nickname, age, favorColor) {
              this.nickname = nickname
              this.age = age
              this.favorColor = favorColor
          }
          Object.defineProperties(Man.prototype,{
              introduce:{
                  value:function(){
                      console.log(`大家好，我是${this.nickname},今年${this.age}岁了,喜欢${this.favorColor}`)
                  },
                  enumerable:false,
                  writable:true
              },
               consturtor:{
                   value:Man
              }
          })
          Man.prototype.some=function(){
              console.log('我是新方法some')
          }
           let aa=new Man('小花',3,'red')
           aa.some()

       第二种情况

      ```js
       let aa=new Man('小花',3,'red')
           aa.introduce()
          Man.prototype={
              some:function(){
                  console.log('我是新的some方法')    //此时已重新对Man的原型赋值了，改变了地址，远啦的地址被覆盖了
              }
          }
           let bb=new Man('小花',3,'red')
          console.log(aa.some)                      //undefined
          console.log(bb.some)                      //我是新的some方法
      ```

      

      **原型链**：如果要去一个变量里面找属性，先去私有属性找，找不到，找原型，找不到，找原型的原型，还是找不到那就找不到了。(所有引用数据类型的原型最后一站都是object，)

      #####  继 承

      ```js
      //共有方法
      function Wanzhang() { }
          Object.defineProperties(Wanzhang.prototype, {
              eat: {
                  value: function () {
                      console.log(`我是${this.nickname}我很喜欢吃`)
                  }
              },
              sleep: {
                  value: function () {
                      console.log(`我是${this.nickname}我很喜欢睡觉`)
                  }
              },
          })
      function Afei(nickname){this.nickname=nickname}
      function Hanlu(nickname){this.nickname=nickname}
      Afei.prototype=new Wanzhang()
      Hanlu.prototype=new Wanzhang()
      const afei=new Afei("小红")
      const hanlu=new Hanlu("小刚")
      afei.sleep() //执行成功
      hanlu.sleep()//执行成功
      ```

      ##### 多 态

      ```js
      Afei.prototype.some=function(){
          console.log('我是新的some方法')
      }
      Hanlu.prototype.earnMoney=function(){
          console.log('我是新的earnMoney方法')
      }
      
      ```

      组合式继承:调用了两次父类构造函数，生成了两份实例（子类实例将子类原型上的那份屏蔽了）

      ```js
      function People(name){
          this.name = name;
      }
      People.prototype.sayHello = function(){
          alert("你好我是" + this.name);
      }
      
      function Student(name,xuehao){
          // console.log(this)
          People.call(this,name);
          this.xuehao = xuehao;
      }
      
      //核心语句，继承的实现全靠这条语句了：
      Student.prototype = new People('小明');
      
      // Student.prototype.study = function(){
      //     alert("好好学习，天天向上");
      // }
      
      var xiaohong = new Student("小红",1001);
      console.log(xiaohong)
      xiaohong.sayHello();
      ```
      
      
      
      寄生式继承:通过寄生方式，砍掉父类的实例属性，这样，在调用两次父类的构造的时候，就不会初始化两次实例方法/属性，避免的组合继承的缺点
      
      ```js
      function People(name){
          this.name = name;
      }
      People.prototype.sayHello = function(){
          alert("你好我是" + this.name);
      }
      
      function Student(name,xuehao){
          People.call(this,name);
          this.xuehao = xuehao;
      }
      
      //核心语句，继承的实现全靠这条语句了：
      function Fn(){}
      Fn.prototype = People.prototype
      Student.prototype = new Fn();
      
      Student.prototype.study = function(){
          alert("好好学习，天天向上");
      }
      var xiaohong = new Student("小红",1001);
xiaohong.sayHello();
      ```

      

      

      

      

      

      
      
      ##### 圣 杯 模 式
      
      ```js
      function A() { }
          Object.defineProperties(A.prototype, {
              drink:{
                  value: function () {
                      console.log("我是A")
                  },
                  writable: true,
                  enumberable: false
              },
              eat:{
                  value: function () {
                      console.log("我是A")
                  },
                  writable: true,
                  enumberable: false
              }
          }
          )
        function B() { }
          B.prototype=new A()
          Object.defineProperties(A.prototype, {
              sleep:{
                  value: function () {
                      console.log("我是B")
                  },
                  writable: true,
                  enumberable: false
              },
              work:{
                  value: function () {
                      console.log("我是B")
                  },
                  writable: true,
                  enumberable: false
              }
          }
          )
          const b=new B()
       function C(nickname) {this.nickname=nickname}
          C.prototype=new B()
          C.prototype.some=function(){
              console.log('我是some')
          }
          const c=new C('小胡')
          console.log(c)
          c.some()
          c.work()
          c.sleep()
          c.eat()
          c.drink()   //c能继承所有的方法
      
      
      
      //第二种,构造函数封装一下
      function inherit(People,Student){
          function Fn(){}
          Fn.prototype = People.prototype
          Student.prototype = new Fn();
          Student.prototype.constructor = Student;
          Student.prototype.parent = People;
      }
      inherit(People,Student )
      ```
      
      
      
      
      
      ### 第十四章：ES6-解 构 赋 值
      
      ​     1**.解构赋值的概念**：只要等号两边的模式类型相同，左边的变量就会被赋予对应的值（注：左右两边的结构格式要保持一致）
      
      例：如果需要数据对应，则需要结构一样、(当左边是一个数组,右边只要是有迭代器,就可以解构成功,例如string类型)
      
      ```js
      let [a,b,c]=[10,20,30]
      console.log([a,b,c])    //[10, 20, 30]
      
      //包装对象解构
      let [a,b]='hello'
      console.log(a,b)    // h e   只要是有迭代器
      ```
```
      
        2.**不成功的解构赋值=>（需要被赋值的数量少于接收值的变量）**
      
      ```js
      //需要被赋值的数量少于接收值的变量
      let [foo] = [];
      let [a,b]=[10] 
      console.log(foo,b)                           //都是undefined  成功
```

      3.**不完全解构=>（就是赋值的变量大于接收值的变量）**
      
      ```js
      let [a,b]=[10,20，30]    //[10, 20]
      let[c,[d],e]=[1,[2,3],4] //[1,[2],4]  成功
      ```
      
         4，**如果模式不匹配，就会报错**
      
      ```js
      let [a]=1;
      let  [b]=false;
      let [c]=NaN;
      let [c]=undefined;
      let [c]=null;
      let [c]={};    //都会报错
      
      ```
      
      5.  **默 认 值：如果定义的变量比较多，而又没有给这变量赋值，那么这个变量就是undefined，但是我们不希望他是undefined，那么就需要用到默认值（解构赋值允许指定默认值）**
      
         ```js
         //第一种情况，没有传值
         let [a,b,c=4]=[1,2]
         console.log(a,b,c)     //1,2,4 此时C的值由于匹配不到右边的值，那么就是默认值
          //第二种情况,后台传值
         let [a,b,c=4]=[1,2,3]  //1,2,3 此时c的值就是后台传的值,不启用默认值
         //第三种情况,后台传的是undefined
         let [a,b,c=4]=[1,2,undefined] //1,2,4 此时如果匹配后台的值为undefined, 那么启用默认值
         //第四种情况,后台传过来的是一个null,表示有值,null表示一个空对象
         let [a,b,c=4]=[1,2,null]  //1,2,null   此时如果后台匹配的值为null,那么不启用默认值,因为null表示有值,只是暂时为空.
                                          
         ```
      
         注意:ES6内部严格使用相等运算符===,判断一个值是否有值,所以,如果数组成员不是严格等于undefined.默认值是不会生效的.  
      
            如果默认值是一个表达式,那么这个表达式是惰性求值的,用到,才会求值
      
         ```js
         function a(){
             console.log('111')
         }
         let x;
         if([1][0]){
             x=a();     
         }else{
             x=[1][0]
         }
         console.log(x)    //111    
         ```
      
         ​     默认值可以用于引用解构赋值的其他变量(前提是该变量是已经申明了的)
      
         ```js
         let [x=1,y=x]=[]  //1,1
         let [x=1,y=x]=[2]  //2,2
         let [x=1,y=x]=[1,2] //1,2
         let [x=y,y=1]=[]     //error报错 因x=y  y没有申明
         ```
      
         利用解构赋值交换两个值=>交换位置
      
         ```js
         let a=5;
         let b=10;
         [a,b]=[b,a]
         console.log(a,b)  // 10,5
         ```
      
         **6、对象的解构赋值**(对象解构赋值属性名必须相同，否则结果为undefined)
      
         ```js
         const obj={
             nickname:'小明',
             age:20,
             sex:'man'
         }
         let {nickname,age,sex}=obj
         console.log(nickname,age,sex)   //'小明',20,'man'
         //如果属性名不同
         let {a,b,c}=obj
         console.log(a,b,c) //undefined undefined undefined
         ```
      
         7.自定义变量名与属性名不同
      
         ```js
         let {name:a,age:b,sex:c}=obj
         console.log(a,b,c) //'小明',20,'man'
         //等同于
         let {nickname:nickname,age:age,sex:sex} = obj; // 这样依然可以改属性名,并打印了解构的值
         console.log(nickname,age,sex);//'小明',20,'man'
         ```
      
         也就是说，对象的解构赋值的内部机制，是先找到同名属性，然后再赋给对应的变量。真正被赋值的是后者，而不是前者。
      
      ​      8.解构可用于嵌套结构
      
      ```js
      let obj={p:['hello',{y:'world'}]}
      let {p:[x,{y}]}=obj
      console.log(x,y)     //hello,world
      ```
      
      ​       对象的解构赋值也可以指定默认值
      
      ​     
      
      ```js
      let {x=3}={}   //3
      let {x, y = 5} = {x: 1};  //x 1,y 5
      let {x: y = 3} = {};      // x 3
      let {x: y = 3} = {x: 5};  // y 5
      
      默认值生效的条件，对象的属性值严格等于undefined
      let {x=3}={x=undefined}  //x=3
      let {x=3}={x=null}       //x=null
      ```
      
      数组也可以按照对象方法结构,对象解构时,不能先定义在,{}={}去解构,{}会被解析成块级作用域=赋值,这样会报错
      
      ```js
      function getPos(){
      	//....
          return {
      		left:10,
              bottom:20
      	}
      }
      let {left,bottom} = getPos();
      console.log(left,bottom);  // 10, 20
      
      // 这里不敢用top,因为全局的top会被当成window对象.所以这个时候就取名就显得格外重要
      
      function getPos(){
      	//....
          return {
      		left:10,
              top:20
      	}
      }
      let {left,top:t} = getPos();
      console.log(left,t); //10 20
      // 如果使用使用top,这里在全局环境下可以使用解构自己定义名字的方式
      ```

​         **9 字符串的解构赋值**

```js
const [a, b, c, d, e] = 'hello';
a // "h"
b // "e"
c // "l"
d // "l"
e // "o"
```

  字符串也可以看做是类数组,因为有length属性,类似数组的对象都有一个`length`属性，因此还可以对这个属性解构赋值。

​      **10.函数参数的解构赋值**

```js
function add([a,b]){
  return a+b;
}
add([2,3])//5
function fn({a,b}){
	console.log(a,b); //1 2
}
fn({
	a: 1,
    b: 2
})
```

​         函数参数解构的默认值

```js
function move({x = 0, y = 0} = {}) {
  return [x, y];
}

move({x: 3, y: 8}); // [3, 8]
move({x: 3}); // [3, 0]
move({}); // [0, 0]
move(); // [0, 0]  如果没传任何值，就启用后边的{}，否则会报错
```

11. **数字和布尔值的解构赋值**

    解构赋值时,如果等号右边是数值和布尔值,则会先转化为对象

    ```js
    let {toString: s} = 123;
    s === Number.prototype.toString // true
    
    let {toString: s} = true;
    s === Boolean.prototype.toString // true
    ```

    知识点：解构赋值可以解构出console.log,等等
    
    ```js
    //解构出log
    const {log}=console
    log('我是新的console.log')  //我是新的console.log
    //解构出获取dom元素的函数:bind绑定
    const {querySelector}=document
    const $=querySelector.bind(document)
     console.log($('.box'))   //注意解构document方法的时候,需要手动绑定this指向,否则会报错,document的方法this必须指向document
       //call绑定
    const {querySelector:$}=document
    console.log($.call(document,('.box')))  //<section class='box'></section>
    ```
    
    <span style='color:red'>注意如果解构的是一个对象，并且改变对象的属性值，需要手动去更改对应的值，否则原对象值不会改变</span>
    
    ```js
    //这个属性值不是引用数据类型的情况,解构赋值以后改变属性值,原属性值不会改变
    let  options={
        moveX:0,
        index:0
    }
    let {index,moveX}=options
    index=2
    moveX=40
    log(index,moveX)       //20,40
    log(options.moveX,options.index)//0,0
    //这个属性值是引用数据类型,
    let some={nickname:{name:'小明',age:3}}
    let {nickname}=some
    log(nickname)
    nickname.name='小刚'
    log(nickname,some.nickname)  //小刚,小刚
    ```
    
    
    
    ### 第十五章   ES6-class 类
    
      1、class类的概念：ES6 的`class`可以看作只是一个语法糖，它的绝大部分功能，ES5 都可以做到，新的`class`写法只是让对象原型的写法更加清晰、更像面向对象编程的语法而已，通过`class`关键字，可以定义类。

​         **ES5之前模拟的类**

```js
// 通过ES5的实现
function Person(nickname){
    this.nickname=nickname
}
Person.prototype.introduce=function(){
    console.log(`我是${this.nickname}introduce方法`)
}
Person.prototype.sleep=function(){
    console.log(`我是${this.nickname}sleep方法`)
}
const p1=new Person('小红')
p1.introduce()
p1.sleep()

//第二种，通过对象的assign方法合并对象实现
Object.assign(Person.prototype,{
    introduce(){
        console.log(`我是${this.nickname}introduce方法`)
    },
    sleep(){
        console.log(`我是${this.nickname}sleep方法`)
    }
})
const p1=new Person('小红')
p1.introduce()
p1.sleep()
```

​      以上两种方法都能实现相应的功能，但是都是ES5，都是在给对象的原型上加方法

​         **ES6 的变形calss类**

####             **1.class类的书写方式：**

```js
  //类的书写方式
    class Person {
        //注意是在constructor里面添加私有属性
        constructor(nickname) {
            this.nickname = nickname
        }
        //在constructor外面为Person构造函数原型上添加公有方法
        introduce(){
            console.log(`${this.nickname}的introduce方法`)
        }
        //不需要加逗号,因为他是类,不是一个json对象,加了就会报错
        sleep(){
            console.log(`${this.nickname}的sleep方法`)
        }
    }
    //同样实例化对象需要通过new
    const p1=new Person('小红')
    console.log(p1) 
     p1.introduce() 
     p1.sleep()     
```

  不推荐表达式的类这种方法

```js
var Person = class {
    constructor(){
        this.name = "wuwei";
    }
    showName(){
        return `名字:${this.name}`
    }
}
```

  注意：constructor方法是默认的方法，通过new实例化的对象自动调用该方法，如果没有显示定义，那么它会自动生成一个空的constructor方法（constructor方法默认返回实例对象（即this））

####     **2.class类里面的静态方法（static）:如果在一个方法前，加上`static`关键字，就表示该方法不会被实例继承，而是直接通过类来调用， 这就称为“静态方法”。**

```js
 class Person {
        constructor(nickname) {
            this.nickname = nickname
        }
        introduce(){
            console.log(`${this.nickname}的introduce方法`)
        }
        sleep(){
            Person.some()
            console.log(`${this.nickname}的sleep方法`)
        }
       //静态方法
        static some(){
            console.log('我是some')
        }
    }
    const p1=new Person('小红')
    console.log(p1)    
      p1.some()      //会报错,实例化出来的对象身上没有some方法,因为some方法是挂载到类Person上的
     Person.some()  //正确写法
```

​     同样,class类里面也有静态属性

```js
      static a='1233'     //同样静态属性也是挂载在Person类上面的,实例化的对象无法调用
```

####    **3.ES6的class类没有提升和预解析的功能**

​    如果这样写,就会报错,找不到Person

```js
var p1 = new Person()
console.log(p1);

class Person{
    constructor(){
        this.name = "aaa"
    }
}
```

####     4.继 承

​     **子类继承父类:关键字->extents**

```js
class  Big{
         constructor(nickname,age){
          this.nickname=nickname,
          this.age=age
         }
         introduce(){
             console.log(`${this.nickname}的introduce方法`)
         }
         sleep(){
            console.log(`${this.nickname}的sleep方法`)
         }
         static some(){
             console.log('我是继承父类的静态方法some')
         }
     }

     class Small extends Big{
         //如果没有写constructor,那么会默认生成一个空的constructor,并且super()
        //  constructor(x,y){
        //    super(),
        //  }
         eat(){
             console.log('我是eat方法')
         }
         earymoney(){
             console.log('我是earymoney方法')
         }
         static abc(){
             console.log('abc')
         }
     }
     const small=new Small(1,2)
     console.log(small)
```

  如果想要添加自己想要扩展的属性和方法,就必须通过super()

```js
 class  Big{
         constructor(nickname,age){
          this.nickname=nickname,
          this.age=age
         }
         introduce(){
             console.log(`${this.nickname}的introduce方法`)
         }
         sleep(){
            console.log(`${this.nickname}的sleep方法`)
         }
         static some(){
             console.log('我是继承父类的静态方法some')
         }
     }
     class Small extends Big{
         constructor(x,y){
           super(x,y),//先执行父类的属性，继承后在设置自己的属性
           //父类帮我们提供了nickname和age属性，我们自己添加了x和y
           this.x=x,
           this.y=y
         }
         eat(){
             Big.some()//静态方法必须是父类调用才有效
             console.log('我是eat方法')
         }
         //继承父类方法同时扩展
         earymoney(){
             super.sleep()//执行父类的sleep方法，在执行自己的earymoney方法
             console.log('我是earymoney子类方法')
         }
         static abc(){
             console.log('abc')
         }
     }
     const small=new Small(1,2)
       small.eat()
```

**5.取值函数get和存值函数set**

```js
class Person{
    constructor(name,age){ 
        this.name = name;
        this.age = age;
    }
    get aa(){
        console.log(`成功获取a的值`)
        return this.age;
    }
    set aa(val){
        console.log(`成功设置a的值为${val}`);
        this.age = val;
    }
}

var p1 = new Person('wuwei',18)
```

   **如果要是用变量,那么就要使用[]的表达式**

###   



## **第十六章：正 则 表 达 式**

  1.什么是正则表达式：正则表达式是字符串的一种匹配模式，专门为简化字符串操作而生，说白了就是为了检索一个字符串中特定字符的规则,正则并不是单纯的字符串,而是一种逻辑公式

  2.创建正则的两种方式

```js
//字面量创建方式
let reg=/ /;
//构造函数创建方式
let reg=new RegExp()//RegExp 其实是由两个单词构成的,regular expression 正规的表达式
```

​    2.1 正则表达式是一个通过内置的构造函数构造出来的对象

```js
let  reg=new RegExp('text')  //实例化一个正则对象
//一共接受两个参数，第一个参数是正则，第二个参数是修饰符 i g m
```

  例

```js
   let reg=new RegExp('text')
   let str='abctext'
   console.log(reg.test(str))  //true  
// test()方法就是以正则为规则检查字符串中是否包含正则内容
```

2.2字面量的方式

```js
let reg=/text/
let str="abc'text'"
console.log(reg.test(str))//true 注意如果在字面量创建的里面加引号，通过正则查找则为false，如果在所要查询的字符串中加引号，则为true
```

3.使用正则时注意的地方：一般情况下我们推荐使用字面量的创建方式，但是如果是变量存储的字符串，则需要用构造函数的方式创建正则

```js
var v = 'text';
var reg = /v/;  		  // 这样写正则就匹配v了
var reg = new RegExp(v);  // 所以这种情况就只能用构造函数方法了
```

  **4.正则表达式的两种方法**

​     1.test方法：正则对象的一个方法，它表示该字符串（参数）是否匹配我们的正则规则

​        使用语法（reg.test(str)）

​      例：

```js
var reg = /wuwei/;
var str = 'hello wuwei';  
// 判断str字符串是否匹配我们reg规则
console.log(reg.test(str));
```

   2.exec：提取匹配成功的子字符串(不能用全局匹配使用)

```js
let reg=/text/
let str='abctextdtexttext'
console.log(reg.exec(str))  //是一个数组，显示第一个子字符串，以及它的下标
```

 可以使用正则的字符串方法：

> ​    1.search 获取字符在字符串中的位置
>
> ​    2.split 字符串转化成数组
>
> ​    3.replace字符串替换

  **5.修饰符**

>    1.i表示不区分大小写  ignorecase
>
>    2.g表示全局匹配    global
>
>    3.m表示换行匹配   multiline

 例：

```js
//不区分大小写字面量方式-i
let str='abctextdtexttext'
let reg=/Text/i
console.log(reg.test(str))
//不区分大小写构造函数方式-i
let str='abctextdtexttext'
let reg=new RegExp('Text','i')
console.log(reg.test(str))
//全局匹配-g
let str='abctextdtexttext'
let reg=new RegExp('text','g')
console.log(str.match(reg))
//换行匹配-m
var reg = new RegExp('^Text','m');  // 实例化一个正则对象
var str = 'This is a \nText and';
console.log(str.match(reg));// ["Text", index: 11, input: "This is a ↵Text and", groups: undefined]
//复合写法
let str='abctext\ndtexttext'
let reg=new RegExp('Text','ig')
console.log(str.match(reg))
```

#####   6,正则表达式的特殊语法

​      正则表达式是由普通字符和特殊字符(元字符)组成

​      1.特殊字符:() [] {} ^ $ * ? \ | + .

​       2.普通字符:数字(123),字母(a-z,A-Z),_等等

​      普通字符可以直接用,但是特殊字符需要转义

例:

```js
//符号^ 转义
let reg=/\^ab/ 
console.log(reg.test('bd^ab'))
//符号\\需要转义
let reg=/\\m/ 
console.log(reg.test('bd\\mb'))// 字符串中反斜杠要转义
```

 预定义的特殊字符

  \t	/\t/	制表符  	

  \n	/\n/	回车符		

  \f	/\f/	换页符		

  \b	/\b/  与回退字符

```js
let reg=/\t/
console.log(reg.test('a\tb'))
```

####   7. 字 符 集

   1.简单类：它是由一一对应的字符组成的集合，用[]包裹,来表示这几个字母组成的一个集合

```js
let reg=/[abcdef]/
let str='jc'
console.log(reg.test(str))  //只要str在字符集中匹配一个成功就是true
```

   2.范围类: 通过首位字母以及-组成的一个范围集合例如:[0-9],[a-z],[A-Z]

```js
let reg=/[f-i]/
let str='abcdeg'
console.log(reg.test(str))  //true
```

按照字符编码集可以从小到达[A-z]  不能从大到小[a-Z],这样写及容易报错

  3.负向类:在[]里面通过在前面加一个^,范围取反

```js
var str = 'fabcdef';
var reg = /[^f]/;
console.log(reg.test(str));//true  只要有一个匹配就为true
```

 4.组合类：在[]里面，有几个范围集合拼接在一起表示一个组合的集合

```js
var str = 'fabcdef';
var reg = /[a-z0-9]/;
console.log(reg.test(str));
```

  注意：中括号的字符集里面无论你写多少个字符只会匹配其中一个，特殊的中文字符集（[\u4e00-\u9fa5]）

5.界定符：字符串是有边界的，这里的边界指的就是首尾。

​    界定字符串首位的是^,界定末尾的是$

```js
let str='abcde'
let reg=/^abcde$/
console.log(reg.test(str))          //true      以abcde开始，以abcde结尾
```

6匹配后边跟的字符

​    1.（？=n）匹配到后面紧跟着n的字符

​     2.（？！n）匹配到后边没有紧跟着n的字符

```js
//b后面紧跟着c的字符
let str='abcde'
let reg=/b(?=c)/
console.log(str.match(reg))
```

####   8 预定义的类（元字符）

​    就是特殊的转移字符,把一些字母转成特殊意义的字符

.    ^\n\r  :除了换行回车之外的任意字符

\d       [0-9]     数字字符

\D     `[^0-9]`	非数字字符

\s      [ \t\n\x0B\f\r]  空白字符

\S    `[^ \t\n\x0B\f\r]`非空白符

\w    [a-zA-Z0-9]       单词字符(所有的字母)

\W	`[^a-zA-Z_0-9]`			非单词字符

 例：

```js
let str='abcdes'
let reg=/ab\d/
console.log(reg.test(str));//false
```

**量词**：无论字符集还是元字符，都只能匹配到一个字符，无法匹配多个字符，所以引入量词的概念，用来设置匹配到字符的个数，用{}

量词普通写法：

1.{n}  表示n个

2.{n-m}表示n到m个，包含n也包含m

3.{n，}n-无穷大。包含n

量词的也是写法

{1，}可有+代替

{0，}可有*代替

{0，1}可有？代替  

 量词的贪婪与惰性， 量词+默认贪婪匹配，就是说尽量往指定范围类最大的匹配，在量词后面加上 `?` 符号，变为惰性匹配，也就是尽量少的去匹配。

**子项**：定义正则时，可以用`()`将部分规则包裹起来，这样在使用match或者exec做匹配的时候，能在得到的结果里面拿到该部分匹配的内容。

```js
var str = "abcd12ef";
var reg = /d(\d+)/;
console.log(str.match(reg));//["b1", "1", index: 1, input: "ab1cdes", groups: undefined]
```

子项反向引用(也叫捕获组)

```js
var str = "ccsdbbcc99d";
var reg = /(c)[a-z]/g;
console.log(str.match(reg));

var str = "ccsdbbcc99d";
var reg = /([a-z])\1/g;        //取出重复的项
console.log(str.match(reg));

```

**或者  |**   在正则中|表示或者

```js
var str = "adcd12ef";
var reg = /ad|cd/g;
console.log(str.match(reg));  // ["ad","cd"]
```

也可以与子项结合使用

```js
var str = "adcd12ef";
var reg = /(a|c)d/g;
console.log(str.match(reg));  // ["ad","cd"]
```

如果放在字符集里面就是普通的|

```js
var str = "adcd1|d2ef";
var reg = /[a|c]d/g;
console.log(str.match(reg));  // ["ad", "cd", "|d"]
```

例子：验证手机号码格式是否正确

```js
let  str='1381278235622'
let reg=/^1[356789]\d{9}$/    //指定开头还结尾,然后指定第二个数字的范围
console.log(reg.test(str))
```

例子:日期变成 2020-04-22 12:23:55

```js
let str='YYYY-MM-DD HH:FF:SS',
    date=new Date();
function  dateFormat(time,newstr){
    let newYear=date.getFullYear()
    newstr=newstr.replace(str.match(/Y+/)[0],(newYear+'').slice(-(str.match(/Y+/)[0].length))) //量词的贪婪写法
    timer={
        getMonth:/M+/,
        getDate:/D+/,
        getHours:/H+/,
        getMinutes:/F+/,
        getSeconds:/S+/
    }
    for(let key in timer){
        newstr=newstr.replace(newstr.match(timer[key])[0],totwo(time[key]()))
    }
    function totwo(num){
      return num>10?num:'0'+num
    }
}
dateFormat(date,str)   //2020-04-22 12:23:55
```

  **例子：验证邮箱是否正确**

```js
   const op = document.querySelector('p'),
            ipt = document.querySelector('input'),
            btn = document.querySelector('button');
        console.log(op, ipt, btn)
        const reg_email = /^\w+[\-_]*\w+@[0-9a-z]{2,}\.com$/
        btn.addEventListener('click', (e) => {
                let value = ipt.value.trim();
                if (reg_email.test(value)) {
                    op.innerText = '登录成功'
                } else {
                    op.innerText = '邮箱格式不正确请重新输入'
                }
                ipt.value = ''
            })
        console.log(reg_email.exec('2164484212@qq.com'))
        console.log(reg_email.exec('merchantliang@gmail.com'))
        console.log(reg_email.exec('han_lu@icloud.com'))
        console.log(reg_email.exec('seven-day@microsoft.com'))
        console.log(reg_email.exec('wq901200@hotmail.com'))
```

例子：屏蔽脏字

```js
    const oipt = document.querySelector('.content2>input'),
            content2 = document.querySelector('.content2'),
            btn = document.querySelector('.content2>button');
        reg_replace = /(我[\s\d_\-+!@#&$]*操)|(脑[\s\d_\-\+!@#&$]残)|(t[\s\d\-\+!_@#&$]m[\s\d\-\+!_@#&$]d)|([\s\d\-\+!_@#&$]b)|(傻[\s\d\-\+!_@#&$]吊)|(傻[\s\d\-\+!_@#&$]屌)|(脑[\s\d\-\+!_@#&$]残)|(你[\s\d\-\+!_@#&$]妹)/;
        //   let arr=[
        //   /我[\s\d\-+!_@#&$]*操/,
        //   /t[\s\d\-+!_@#&$]m[\s\d\-+!_@#&$]d/,
        //   /s[\s\d\-+!_@#&$]b/,
        //   /傻[\s\d\-+!_@#&$]吊|/,
        //   /傻[\s\d\-+!_@#&$]屌/,
        //   /脑[\s\d\-+!_@#&$]残/,
        //   /你[\s\d\-+!_@#&$]妹/
        //   ]
        btn.addEventListener('click', (e) => {
            e.preventDefault();
            e.stopPropagation();
            let value = oipt.value.trim()
            const op = document.createElement('p')
            console.log(value)
            console.log(reg_replace.match(value))
            // if (reg_replace.test(value)) {
            //     value = value.replace(reg_replace.exec(value)[0], '*'.repeat(reg_replace.exec(value)[0].length))
            // }
            op.innerText = value
            content2.append(op)
            oipt.value = ''
        })
```



### 第十七章  async&&await

​      **1.认识async：async的作用是为了让处理异步变得更加简单** ，async和promsie一样本身是同步代码，是ES8引入的为了更简单处理异步

​     1.1   **async的用法：**

```js
    const {log}=console
    async function foo(){
    }
    const some=async ()=>{
    }
   log(some(),foo())  //Promise {<resolved>: undefined} Promise {<resolved>: undefined}打印的是2个promise,如果async函数里面什么都没写,则返回的状态是resolved
```

​     1.2  **async函数里面通过return向then里面传递成功的数据**

```js
 const {log}=console
    async function foo(){
        return 123
    }
    const some=async ()=>{
        return 456
    }
    foo().then((data)=>{
        log(data)
    })
    some().then((xtz)=>{
        log(xtz)
    })
```

   1.3 async何时会走到catch:1.当async里面代码报错,2.在异步的时候出错

```js
  const {log}=console
    async function foo(){   //不能办法手动决定状态,默认都是成功状态执行
        throw new Error('我是foo的错误')
         log(123)   //当在async函数里面用catch捕获错误,会截断后面代码运行
    }
    foo().then((data)=>{
        log(data)
    })
    foo().catch((err)=>{
        log(err)
    })
```

  1.4 async函数里面的一个重要关键字:await等待+promise(异步处理):await后面的promise会决定async的状态

```js
const some=async()=>{
    let result=await new Promise((resolved,reject)=>{
        log('我是some内部的promise')
        reject('失败了')
    })
    log(result)   //这里不执行,当状态为失败之后,阻断了后面代码执行
}
some().catch((err)=>{
    log(err)            //失败了
})
```

   1.5 如果在async函数里面promise状态为reject时,想要不阻断后面代码执行可以 把catch加到await promise后面

```js
const some=async()=>{
    let result=await new Promise((resolved,reject)=>{
        log('我是some内部的promise')
        reject('失败了')
    }).catch((err)=>{
    log(err)
})
    log(12)
}
some()    //我是some内部的promise  失败了   12
```

 1.6await 会返回后面promise成功后的结果

```js
const some=async()=>{
    let result=await new Promise((resolved,reject)=>{
        log('我是some内部的promise')
        resolved('成功了')
    }).catch((err)=>{
    log(err)
})
    log(result)   //成功了
}
some()              
```

 1.7 如果我们等待的不是promise,则被等待的东西会被浏览器写到一个新的promise里面,而且被浏览器创建的这个promise状态一定是成功

```js
const some=async()=>{
    let result=await setTimeout(()=>{
             log('我是settimeout')
    },1000)
    log(result)
}
some()     // 1    我是settimeout
//等同于
 let result=await new Promise((res,rej)=>{
     let something=setTimeout(()=>{
             log('我是settimeout')
    },1000)
     res(something)
 })
    log(result)
```

**分析,当await后面跟的不是一个promise时,会自动被浏览器写到一个promise里面,然后进行res,先执行settimeout的序号,然后在执行延时器里面的代码.所以不建议这么使用async和await.**

   **1.8. async里面的await可以await无数个promise,但是每个promise前面都要写一个await,当async里面有很多个promise时,一旦其中有一个失败,那么整个都失败**

  例:

```js
const some=async ()=>{
     let result1=await new Promise((res,rej)=>{
        setTimeout( () => {
                res( {nickname: '小明'} );
            }, 1000 )
     });
     let result2=await new Promise((res,rej)=>{
        setTimeout( () => {
                res( {nickname: '小刚'} );
            }, 1000 )
     });
     let result3=await new Promise((res,rej)=>{
        setTimeout( () => {
                rej( {nickname: '小花'} );
            }, 1000 )
     })
     log(result1,result2,result3)
 }
 some().catch((err)=>{
     log(err)
 })                       //当有一个失败,则会阻断后面代码执行,返回错误信息
```

 我如果想要失败了一个还需要继续执行async里面后面的代码,则可以这样操作

```js
let result1=await new Promise((res,rej)=>{
        setTimeout( () => {
                res( {nickname: '小明'} );
            }, 1000 )
     }).catch((err)=>{
     log(err)
     });
     let result2=await new Promise((res,rej)=>{
        setTimeout( () => {
                res( {nickname: '小刚'} );
            }, 1000 )
     }).catch((err)=>{
     log(err)
     });
     let result3=await new Promise((res,rej)=>{
        setTimeout( () => {
                rej( {nickname: '小花'} );
            }, 1000 )
     }).catch((err)=>{
     log(err)
     })
     log(result1,result2,result3)
 }        //{nickname: "小花"}   {nickname: "小明"} {nickname: "小刚"} undefined
```

  如果我想要全部一起执行,可以用promise.all

```js
const some=async ()=>{
     let result1= new Promise((res,rej)=>{
        setTimeout( () => {
                res( {nickname: '小明'} );
            }, 1000 )
     }).catch((err)=>{
     log(err)
     });
     let result2=new Promise((res,rej)=>{
        setTimeout( () => {
                res( {nickname: '小刚'} );
            }, 1000 )
     }).catch((err)=>{
     log(err)
     });
     let result3= new Promise((res,rej)=>{
        setTimeout( () => {
                res( {nickname: '小花'} );
            }, 1000 )
     }).catch((err)=>{
     log(err)
     });
    let result4=await Promise.all([result1,result2,result3])
      console.log(result4)
 }
 some()  //1s后打印全部
```

建议,凡是在工作中,ajax请求都用async套起来-> 以同步代码的方式去书写，然后代码还能从上到下按顺序执行.



面试案例:

```js
//同步队列   异步队列( 1微[promise, async]， 2宏[定/延时器] )
//async a   创造async a  执行 顺序问题 -> 同步代码和异步代码的理解
async function a() {
console.log(1);
await new Promise(resolve => resolve());//P2 等待P2的resolve
console.log(2);
}
new Promise( res => {//P1 
console.log(3)
res()
}).then( () => {//P1的then
console.log(4)
new Promise( resolve => resolve() ).then( () => {console.log(5)} )//P3的then
})

setTimeout( () => {
console.log(6)
}, 0 )
a()
console.log(7)
//结果为 3 1 7 4  2 5 6
```





### 第十八章：数组和对象的ES6扩展

​       1.数组的...操作符(展开操作符)

```js
//方式一
const arr=[1,2,3]
  console.log(...arr)  //1,2,3
//方式二:只能把一维数组展开
const arr=[1,2,3,[4,5,6]]
  console.log(...arr)

```

​          展开运算符可以展开的数据:凡是有迭代器接口的数据(例:字符串,数组,类数组……)

​      函数的扩展

```js
function add(...arr){
 log(arr)               // [1,2,3,4]
}
add(1,2,3,4)   
```

扩展运算符可以写在那些地方

>   不能单独写：把一个数据展开之后要有存放的容器
>
>    容器的类别：函数传实参的时候，函数传形参的时候使用，数组里面，用在解构赋值{[]}里面

可以把展开的数据放到一个新数组里面,实现拷贝功能->浅拷贝,相当于数组的concat方法

```js
let arr=[1,2,3,4]
let arr2=[...arr]
log(arr2)
//等同于
let arr=[1,2,3,4]
let arr2=arr.slice()

let arr=[1,2,3,4]
let arr2=[].concat(arr)
```

高版本的代码如何转化为低版本的代码:babel

...操作符可以把类数组转化为真正的数组,从而使用数组的方法

```js
boxs.length = 3;
    console.log(boxs);
    const boxList = [...boxs];
    console.log(boxList);
    let result = boxList.pop();//这里就可以用数组方法删除或者添加元素
    console.log(result);
```

如果在一个函数的形参前面加了...操作符,那么这个形参叫做函数的rest参数[其余]

```js
function add(...rest){
 log(rest)               // [1,2,3,4]
}
add(1,2,3,4)   
```

  实现累加和,可以用...扩展操作符简单完成

```js
funcion sum3(...rest){
    return rest.reduce((acc,item)=>acc+item)
}
sum3(1,2,3,4)     //10
```

  rest参数把没有形参接受的实参全部放到了一个空数组里(rest参数必须是最后一个形参)

```js
function sum4( a, b, ...rest ){//rest参数把没有形参接收的实参全部放到了一个数组里边
        console.log(a,b,rest);
    }
    sum4(1,2);    //1,2,[]
```

2.对象的扩展

​     1.如果对象里面的属性名和属性值相同,则可以简写,只写一个属性名就行

```js
foo='xiaoming'
// let  obj={foo:foo}
let  obj={foo}  //等同于
console.log(obj.foo)

//例2
    let username = 'hanlu';
    let passworld = '123';
    let userInfo = {
        username: username,
        passworld: passworld
    };
    let user_info = { username, passworld };
    log( userInfo, user_info );//结果一样
```

  2.如果对象里面是一个方法,也可以这样简写

```js
const obj={
    nickname:'tony',
    age:2,
    introduce:function(){
        console.log('introduce')
    }
}
obj.introduce()  //introduce

//简写
const obj={
    nickname:'tony',
    age:2,
    introduce(){
        console.log('introduce')
    }
}
obj.introduce()   //introduce
```

3.不仅对象的属性值可以是一个变量,对象的属性名也可以是一个变量(但必须用[]括起来)

```js
let abb = 'hello world';
    let obj6 = {
        [abb]: 123
    };
    console.log(obj6);   //{helloworld:123}
//对象里面的属性名也可以写表达式
    let obj7 = {
        [true ? 123 : 789]: 456
    };
    log(obj7);
```



### 第十九章：symbol和proxy（代理）

#### 一、Symbol

1. **Symbol:它是一种新的简单数据类型（ES6新增），ES5有五种简单数据类型：数字类型number，字符串类型string，布尔类型boolern，undefiend，null，五种简单数据类型，第七种：引用数据类型->（对象obj、数组array，函数function）**

2. **Symbol的主要作用，为了让某个属性或者方法独一无二的存在**

​        对象属性的查找规则：先在私有属性上找，找不到再到原型上找，如果私有属性上有，则不会去找原型的，为了解决覆盖的问题。

 例：

```js
//Symbol不是一个构造函数，所以前面不能加new调用
 const {log} = console
 let symbol = new Symbol('123')
 log(symbol)    //报错,Symbol is not a constructor

//正确声明一个Symbol
 let symbol=Symbol('345')
 log(symbol)    //Symbol(345)
```

1.symbol也是用typeof去判断类型

```js
let symbol=Symbol('123')
log(typeof symbol)    //symbol
```

2.symbol是独一无二的存在

```js
 //定义两个symbol值，哪怕值一模一样，他们也是两个完全独立的，不相等
 let symbol = Symbol('123')
 let symbol2 = Symbol('123')
 log(symbol === symbol2)  //false
//特殊情况：如果是symbol赋值，则相等
let symbol = Symbol('123')
let symbol2=symbol
log(symbol===symbol2)      //ture
```

3.symbol是一个简单数据类型，可以给Symbol里面传一个字符串实参，可以在Symbol里面传任意的数据类型，只要不是字符串，Symbol都会把它转化为字符串

```js
let obj2 = [123, 456];
 let s4 = Symbol(obj2);
  console.log(s4);     //symbol（123，456）
let obj2 = {age：456};
 let s4 = Symbol(obj2)
console.log(s4)      //symbol[object,Object]
```

4.symbol不能和其他任何的数据类型进行计算

```js
console.log( s4 + 1 );   //报错  Cannot convert a Symbol value to a number
 console.log( s4 * 1 );  //Cannot convert a Symbol value to a number
 console.log( s4 + 'hello' );//Cannot convert a Symbol value to a number
 console.log( s4 / true );  //Cannot convert a Symbol value to a number
```

5,symbol当做对象的属性名:在ES5里面对象的属性名都是字符串,es6里边对象的属性名除了可以是字符串之外，还可以是Symbol类型

```js
 let   symbol = Symbol('123')
        let obj2 = {
            [symbol]: '小明',
             age: 3
        }
        log(obj2[symbol]);  //'小明'


 let symbol = Symbol('introduce')
        let obj2 = {
            nickname: '小明',
            age: 3,
            [symbol]() {
                console.log(this.nickname, this.age)
            }

        }
        log(obj2[symbol]());//小明,3
```

6.Symbol.iterator迭代器

```js
let arr=[1,2,3]
for(let key of arr){     //在for of循环数组的时候，用的就是数组的迭代器
    console.log(key)
}
```

7.可以手动的将Symbol转化为字符串

```js
 let int = Symbol('introduce')
 console.log( int.toString() );// Symbol(introduce)
 console.log( int + 'hello' );   //报错，不能运算，
```

8.Symbol类型的数据，如果作为对象的属性，不属于私有属性

```js
 let sss = Symbol('abc');
 let obj9 = {
     nickname: '小明',
     age: 3,
     [sss]: 'abc'
     };
    console.log(obj9);        //{nickname: "小明", age: 3, Symbol(abc): "abc"}
     //没有遍历出来，因为Symbol不是私有属性
    for( let key in obj9 ){
       console.log( key );     ////nickname,age
     };
```

#### 二、proxy（代理）

​     1、proxy[代理]:可以重新定义javascript里面的一些行为，也叫元编程，修改编程语言本身。

​          proxy能重新定义对象（{}）和函数的一些行为

​          proxy的语法:new Proxy(origin,handle)->origin[源对象] ,handle({})要重新定义哪些行为

​     2.get()方法里面 被传了三个实参:target[原对象],propety[原对象的属性]第三个不重要

```js
  let obj1 = {
                nickname: '小刚',
                age: 3
            }
            let p1 = new Proxy(obj1, {
                get(target, prop, receiver) { //获取行为 重新定义行为写在函数里边 target[源对象]
                    console.log(target, prop, receiver); //被传了三个实参
                    // return 36
                }
            });
console.log(p1.nickname, p1.introduce); //我们要通过proxy返回的对象才能使用重新定义的行为
```

小例子:可以通过get拦截器生产dom结构

```js
 const dom = new Proxy({}, {
            get(target, prop) {   //获得两个参数
                return function(abc) {   //传入需要在标签里面显示的文字
                    const aa = document.createElement(prop)
                    aa.innerText = abc
                    return aa
                }
            }
        })
        console.log(dom.p(123))
```

 3.set（）方法：设置target源对象，propety设置的是原对象的哪个属性，value设置的值是什么

```js
let p=new Proxy({},{
    set(target,prop,value){
        console.log(target,prop,value) //target[原对象],prop[属性],value[属性值]
    }
})
p.nickname='小明'  //设置对象的属性
console.log(p)  //{}__proto__: Object "nickname" "xiaoming"
```

​     set方法如何设置值

```js
const obj={
    nickname:'小明',
    age:3
}
let p=new Proxy(obj,{
    set(target,prop,value){
        if(prop==='age'&&value<200){
            target[prop]=value
        }else{
        throw new Error('年龄不能超过200岁')
        }
    }
})
p.age=50
console.log(p)   //Proxy {nickname: "小明", age: 50}
```

 通过set方法如何实现数据绑定

```js
const box=document.querySelector('.box')
const obj={
    nickname:'小明',
}
let p=new Proxy(obj,{
    set(target,prop,value){
            target[prop]=value
            box.innerText=value
       
    }
})
box.innerText=p.nickname
console.log(box)
p.nickname='小刚'
p.nickname='韩麓'    //无论怎么改变.box的innerText值始终绑定在obj的nickname属性值
```

   apply 给函数用的 当调用一个函数的时候，或者call，apply去执行一个函数的时候，会走到apply这一层

```js
let somefn=new Proxy(function(){console.log(this)},{
     apply(target,ctx,arguments){
       console.log(target,ctx,arguments)
       if(ctx===undefined){
           target.call({nickname:'wuwei'},...arguments)
       }else{
           target()
       }
     }
})
somefn(1,2,3)   //改变了this指向
```

 通过Proxy里边的 apply可以重新定义函数的执行，apply和call

```js
let someFn2 = new Proxy( function () { console.log(123) }, {
        apply(target, ctx, args) {//target被执行的那个函数,ctx小明函数里边的this，args所有实参
            console.log(target, ctx, args);
            target();
        }
    } )

    someFn2.call({ nickname: '小刚' })
```

**小案例,通过get方式设置添加dom元素**

```js
const dom=new Proxy({},{
    get(target,prop){
        return function(attr={},...children){
            console.log(attr,children)
            //创建dom元素
            const el=document.createElement(prop)
            //通过遍历为dom元素添加属性和属性值
            for(key in attr){
                el.setAttribute(key, attr[key])
            }
            //循环数组判断是否为字符串类型添加文本节点进去
            children.forEach((item)=>{
                if(typeof item==='String'){
                    item=document.createTextNode(item)
                }
                el.append(item)
            })
            return el
        }
    }
})
  const aa= dom.div({class:'box'},'helloworld',dom.a({href:'#'},'maxname',dom.img({src:'',target:'#'},'我是图片')))                 //从后往前执行  
  document.body.append(aa)
  const ba= dom.section({class:'box'},'hello world',dom.ul({},dom.li({},'我是图片'),dom.li({},'我是图片'),dom.li({},'我是图片'),dom.li({},'我是图片')))
  document.body.append(ba)
```







### 第二十章： Math方法

   **1.Math的常用方法**

> ​       abs(num):绝对值 ,
>
> ​       floor(num):向下取整,
>
> ​      ceil(num):向上取整.
>
> ​      max(num1,num2,……): 从多个数字里面取最大值;
>
> ​      min(num1,num2……):从多个数字里面取最小值;
>
> ​      pow（num，x）：num的x次方
>
> ​      random（传值也没用）：随机生成一个[0,1)之间的数字,小数部分最多17位 实际有可能是1；
>
> ​     round（num）：四舍五入；
>
> ​      sing（num）：返回这个数字的符号，正数返回1，负数返回-1.+0返回0，-0返回-0，NAN

例：用两种方法找到数组里面的最小值

```js
 let arr = [123,143,4,6,24,37,3,567867,1,-5,4,52,346,5,4,56,67,3,364,74,535];
    // //用两种方法找到这个数组里边的最小值
     console.log( Math.min(...arr) );//-5
     console.log( Math.max(...arr) );//567867
     //...操作符：可以写在： 数组，数组匹配模式，形参，实参(rest参数)
     console.log( Math.min.apply(null, arr) );//apply是以数组的形式传参，内部会把数组的每一项都变成一个实参
    console.log( Math.max.apply(null, arr) );
```

随机生成一个数字范围：

```js
//有个公式
Math.random() * (max-min) + min
```

 例：在12首歌曲里面，让它们随机播放，

```js
console.log(Math.ceil(Math.random()*12))
如何保证生成过的数字不重复 -> []
    // do{
    //     //先执行以下这里的代码
    // }while()//然后再判断是否停止
```





### 第二十一章：模块化（module）

  1.什么是ES6模块化：每一个js文件都是独立的，其它js文件无法去用别人的东西，模块化的主要作用就是为了去打通模块之间的壁垒，让它们之间可以相互使用。

 2.模块化有两个关键字：export（导出），import（导入）

  3.注意：statement声明

​           报错信息：Cannot use import statement outside a module 不能在模块之外去使用import声明，我们需要在引入模块化js文件时，加上type=‘module’，并且在liveserve中打开，否则有跨域问题。

##### 1.export的书写规范&如何正确导出方式

```js
 //export的常用书写方式
//第一种;直接导出
1.export   const a=123  //正确
2.export   const b=[1,2,3] //正确
3.export   const c={nickname:'小明'};
4.export   const function fn(){
    console.log('fn')
}
//第二种;集中导出
const d = { nickname: '小刚' };
const e = () => { console.log('我是e') };
const f = 'hello world';
export { d, e, f };

//被导出的东西,值是实时变化的
export let foo={name:'foo'};
setTimeout(()=>{
    foo={name:'bar'}
},1000)

//默认导出
const some={name:'some'};
export default some;//往module里边添加了一个default属性,值是some的值

//这种写法引入的是index模块默认导出的值
import React from './index.js';//随便给默认导出的值命名
console.log(React);
```

**注意:默认导出,只能使用一次,不能使用多次**

​     **2.import:导入的书写规范 &&正确的方式**

​       语法:import  {导出什么} from '路径'(相对路径和绝对路径)

​         //在导入其他模块变量的时候用as重新命名,不能使用默认值

```js
//把进口的东西放在一个对象里边
import { d, e, f } from './index.js';
console.log(d, e, f);

//如果需要改变import对象里面的属性名：则需要用as不能直接加：
import {
    a as aaa, 
    b as bbb, 
    c, 
    fn
} from './index.js';//把要进口的东西放在一个对象里边
console.log(aaa, bbb, c);
```

import（导入）的时候除了可以指定要导入的东西之外，还可以导入index.js里面全部导出的东西

​    *表示全部的东西，需要单独取一个名字用as

```js
import * as all from ‘./index.js’
```

   注意：如果重复导入同一个js模块里的东西，那么在编译的时候只会导入一次，相当于把几次要导入的东西合并在一起导入，

```js
import {a,b,c} from './index.js'
import {d,e,f} from './index.js'
//等同于 
import {a,b,c,d,e,f} from './index.js'
```



**import是静态加载的-》js是编译型语言(执行之前先过一遍,第二遍读的时候才执行)**

**import在第一次读的时候执行**

```js
fn_a();       //可以执行,
console.log(some_a);
import { fn_a, some_a } from './index.js';//静态加载,已经执行了
```

弊端:import不能写在函数,for循环,判断……里面，不能动态的引入数据

```js
let some = 'add';
if( some === 'add' ){
  import {add} from './index.js';
}else{
     import {acc} from './index.js';  //报错,不期望出现的标识符,第一遍已经执行了,ifelse是第二次执行
 }
```

如何解决这个问题:可以用 import('路径'),动态引入

```js
let some = 'acc';
if( some === 'add' ){
    import('./index.js')    //打印它是一个promise,那么就可以调用.then方法获取值
        .then( data => {
            const {add} = data;    //通过解构,得到该值
            console.log(add)
        } )
        .catch( err => {           
            console.log(err)
        } )
}else{
    import('./index.js')
        .then( data => {
            const {acc} = data;
            console.log(acc)
        } )
        .catch( err => {
            console.log(err)
        } )
};                           //这种方式就可以动态获取
```

导入和导出的值都是实时更新的

```js
import {foo} from './index.js';
console.log(foo);
setTimeout( () => {
    console.log(foo)
}, 1000 );
```

如果同时引入默认值和变量可以这样处理

```js
import  default，{a，b，c} form ‘./index.js’
```

### 第二十二章：window（BOM）

   **1.什么是window：浏览器对象模型，每个标签页都有一个独立的window，他们之间互不干扰**

​    **2.window屏幕的左上角**（0，0）

> ​       1.screenTop：整个屏幕中的Y轴坐标（全部兼容）
>
> ​        2.screenLeft：整个屏幕X轴的坐标（全部兼容）
>
> ​        3.screenX：和screenLeft是一样的（有兼容问题）
>
> ​        4.screenY：和screenTop一样（有兼容问题）

移动浏览器：

> ​        1.moveTo（x，y）：让浏览器移动到哪里
>
> ​        2.moveBy（x，y）：以当前位置为起点，进行移动
>
> ```js
> //被浏览器禁止了
> window.moveTo(500,500)   //不会移动
> window.moveBy(100,100)    //不会动
> ```

浏览器可视区域的大小

> 1.window.innerWidth:浏览器**可视区域**的宽度(不包括被撑开的内容)
>
> 2.window.innerHeight:浏览器**可视区域**的高度(不包括被撑开的内容)

监听页面可是区域发生变化:window.onresize

```js
window.onresize=function(){                       用事件监听动态改变可视区域大小
    box.style.cssText=`width:${window.innerWidth / 2}px;height:${window.innerHeight / 2}px;`
}
```

**也可以在css里面通过 VH和VW来设置，实时获取变化的大小**=>（每一个VH代表1%）

  **3.window.open(**url,method,name,'options')打开一个新窗口,method:_self(当前页面),_blank(新开一个窗口)(会被拦截)

```js
 //let result = window.open('https://www.baidu.com', '_blank','baidu', 'width=300,height=300,top=10,left=10');//不能返回
    // console.log(result);
    // result.moveTo(0, 0);
    // result.moveBy(100, 100);
```

####  4.*window.location->window里面使用最多的属性

> ​        1.Location对象:和当前页面路由有关的一切信息
>
> ​         2.hash:哈希值 如果请求不到资源,不会给我们显示空白页面（不会跳转到新页面，在单页面应用，一般是加#/例如"https://www.taobao.com#/abcd" ）
>
> ​          3.host 域名和端口号( "www.taobao.com" )
>
> ​          4.href完整的url(统一资源定位符)( "https://www.taobao.com" )
>
> ​          5.pashname:路径
>
> ​          6.port:端口号  没有写默认是80
>
> ​          7.protocol:协议
>
> ​          **8.search**:查询->查询路由里边的数据拼接
>
> ​         9.origin：https://www.taobao.com+端口号

如何通过window.search查询到的数据转化成对象格式

```js
const search='nickname=小明&age=5'
function searchToObj(str){
    str=str.slice(1)
    str=str.map(item=>item.split('='))
    return Object.fromEntries(str)  //数组转对象的方法
}
searchToObj(search)
```

  Location.assign(url)跳转到一个新的网页-》可以返回上一页，只能在本页跳转

  location.href=url效果和  Location.assign(url)一样

  location.reload():刷新当前页面

   **history  历史对象=>所有浏览记录都保存在history里面**

​       History {length: 1, scrollRestoration: "auto", state: null}  length:一共有多少条历史记录

​       back():返回,只能退一

​       forward():前进,只能进一

​       go(num)如果是一个正数前进多少页,负数就是倒退到第几页





## 第二十三章:canvas

​           1：canvas是一个画布:就是一个图片,保存的时候格式为png,在使用时需要告诉浏览器,是画2d还是3d的画,canvas必须结合js才有效果.  它是一个HTML5最受欢迎的新标签(是一个行内元素,本身是透明的,默认宽高:300*150)  (Webgl)

​          2:canvas中 2d的画布提供了一个内置的图形->矩形(rect)

​          使用canvs画图流程分为以下几点:

​             1.2d/3d:获取上下文  canvas.getContext('2d')

​             2.可以用canvas画矩形:fillRect ->实心矩形 ，stokeRect->虚心矩形（描边矩形）

```js
const rect = document.querySelector('.rect')
        //获取上下文，画布是画什么的
    const rect_con = rect.getContext('2d')
        //填充矩形颜色(需要在绘制图形前先设定颜色，才会显示)
    rect_con.fillStyle = "blue"
        //绘制矩形区域，需要传入4个参数（X轴，y轴，宽度，高度）
        //实心矩形
    rect_con.fillRect(50, 50, 100, 100)
        //填充虚心矩形的颜色
    rect_con.strokeStyle = "red"
        //虚心的矩形
    rect_con.strokeRect(80, 80, 150, 150)
    //清除矩形,实心的矩形能全部清除掉,但是虚心的矩形无法全部清除
    rect_con.clearRect(50, 50, 100, 100)
```

   如果画的图形区域超出画布的整个宽度和高度,则超出部分会被隐藏掉,可以重复画,后边的层级会比前面高,前面的会被覆盖掉

```js
rect_con.fillStyle = "blue"
        //绘制矩形区域，需要传入4个参数（X轴，y轴，宽度，高度）
        //实心矩形
    rect_con.fillRect(200, 200, 100, 100)
    rect_con.fillStyle = "pink"
    rect_con.fillRect(200, 200, 100, 100)  //显示pink的图形
```

​    3.如何绘制阴影:

> ​     1.shadowColor:用css颜色格式表示的阴影色,默认是黑色
>
> ​     2.shadowOffsetX:水平方向偏移量;
>
> ​    3.shadowOffsetY:竖直方向偏移量;
>
> ​    4.shadowBlur:模糊的像素,默认为0;



```js
 //绘制阴影
    const rect1 = document.querySelector('.rect1')
    const con2 = rect1.getContext('2d')
        //必须在绘制前，设定模糊系数,否则会没作用
    con2.shadowBlur = 5;
    con2.shadowColor = 'purple'
    con2.shadowOffsetX = 10
    con2.shadowOffsetY = 10
    con2.fillStyle = 'pink'
    con2.fillRect(50, 50, 100, 100)
    //如果想要后面的绘制的图形不再有阴影，直接设置阴影颜色为透明就好了
    con2.shadowColor = 'transparent'
    con2.fillRect(200, 200, 100, 100)
```

**4.渐变:分为线性渐变和径向渐变两种:**

​      **4.1 线性渐变(linear-gradient):**

​        const linear = context.createLinearGradient(矩形区域的x1, 矩形区域的y1, 矩形区域的x2, 矩形区域的y2)

​          linear.addColorStop(0, '颜色')起点颜色

​          linear.addColorStop(1, '颜色')终点颜色

```js
//线性渐变-linear-gradient
    const rect1 = document.querySelector('.rect1')
    const con2 = rect1.getContext('2d')
        //创建线性渐变，调用addColorStop添加起始位置，颜色和终止为止，颜色
        //createLinearGradient(开始的x轴坐标，开始的y轴坐标，终止的x轴坐标，终止的y轴坐标)
    const linear = con2.createLinearGradient(0, 0, 100, 100)
    linear.addColorStop(0, 'red')
    linear.addColorStop(1, 'blue')
        //需要把线性渐变给到填充的颜色
    con2.fillStyle = linear
        //绘制的区域大小
    con2.fillRect(0, 0, 100, 100)
```

  **4.2 径向渐变(Radial-Gradient):**

​            const radial = context.createRadialGradient(第一圈圆的x坐标，第一圈圆的y坐标，第一圈圆的半径，第二圈圆的x坐标，第二圈圆的x坐标，第二圈圆的半径)

​          linear.addColorStop(0, '颜色')起点颜色

​          linear.addColorStop(1, '颜色')终点颜色

```js
//径向渐变-radial-gradient
    const rect1 = document.querySelector('.rect1')
    const con2 = rect1.getContext('2d')
        //创建线性渐变，调用addColorStop添加起始位置，颜色和终止为止，颜色
        //createLinearGradient((第一圈圆的x坐标，第一圈圆的y坐标，第一圈圆的半径，第二圈圆的x坐标，第二圈圆的x坐标，第二圈圆的半径))
    const radial = con2.createRadialGradient(100, 100, 20, 100, 100, 40)
    radial.addColorStop(0, 'red')
    radial.addColorStop(0, 'yellow')
    radial.addColorStop(1, 'blue')
        //需要把径向渐变给到填充的颜色
    con2.fillStyle = radial
        //绘制的区域大小,如果渐变色的区域小于包裹区域，那么最后一层颜色就会传导出去
    con2.fillRect(60, 60, 300, 300)
```

 4.3 圆形：

​          beginPath() 开始画圆

​          moveTo(x, y)游标的位置 抬起笔尖

​          arc(圆形x, 圆形y, 开始角度(弧度), 结束角度(弧度), 顺时针(false)还是逆时针(true))圆

​         moveTo(x, y)游标的位置 抬起笔尖

​          closePath() 结束路径

​          stroke.Style(),颜色

​          stroke()开始画

```js
 //绘制圆形  arc
    //beginPath（）：开始画圆， closePath()：结束画圆
    const rect1 = document.querySelector('.rect1')
    const con2 = rect1.getContext('2d')
        //开始路径
    con2.beginPath()
    con2.arc(150, 150, 100, 0, 2 * Math.PI, false)
        //结束路径
    con2.closePath();
    //开始画,实心/空心,填充的颜色
    con2.strokeStyle = 'red'
    con2.stroke()
        //抬起笔尖,移动
    con2.moveTo(230, 150)
    con2.beginPath()
    con2.arc(150, 150, 80, 0, Math.PI / 3, false)
        //结束的时候,抬起笔尖,移动,让其不要连回去
    con2.moveTo(170, 230)
    con2.closePath();
    con2.strokeStyle = 'skyblue'
    con2.stroke()

```

​     －> 直线：

​                moveTo(x, y)游标的位置 抬起笔尖 -> 从哪里开始画直线

​                lineTo(x, y) 绘制结束点的x坐标和y坐标 -> 画到哪里结束

​            -> 绘制文本:

​                font：'字体大小 字体'

​                textAlign: start center end

​                textBaseline: top bottom middle

​                fillText('要绘制的文字', x, y)实心文字 strokeText('要绘制的文字', x, y)虚心文字

```js
// 绘制圆形  arc
    // beginPath（）：开始画圆， closePath()：结束画圆
    const rect1 = document.querySelector('.rect1')
    const con2 = rect1.getContext('2d')
        //开始路径
    con2.beginPath()
    con2.arc(150, 150, 100, 0, 2 * Math.PI, false)
        //结束路径
    con2.closePath();
    //开始画,实心/空心,填充的颜色
    con2.strokeStyle = 'red'
    con2.stroke()
        //抬起笔尖,移动
    con2.moveTo(230, 150)
    con2.beginPath()
    con2.arc(150, 150, 80, 0, 2*Math.PI, false)
        //结束的时候,抬起笔尖,移动,让其不要连回去
    // con2.moveTo(170, 230)
    //分针
    con2.moveTo(150,150)
    con2.lineTo(150,85)
    //时针
    con2.moveTo(150,150)
    con2.lineTo(90,150)
    con2.closePath();
    //填充文字
    con2.strokeStyle = 'green'
    //设置文字的位置
    con2.textAlign='center'
    //字体大小,字体
    con2.font='20px sans-serif'
    //设置文字
    con2.strokeText('12',150,80)
    con2.strokeText('9',80,154)
    con2.strokeStyle='purple'
    con2.stroke()
```


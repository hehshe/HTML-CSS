## css基础知识

### CSS简介

Cascading Style Sheets，简称**层叠样式表**，主要是用来进行**页面的版面布局**和**外观样式的美化**；

### css体验

书写一个div嵌套“我们是可爱的程序员”，然后通过css设置文字大小为80px，文字颜色为红色；

![](assets/01.png)

```html
    <style>
        div {
            font-size: 80px;
            color: red;
        }
    </style>
    <div>我们是可爱的程序员</div>
```

## 二、css的书写位置

css可以通过三种方式引入到项目中：最主是行内样式、内部样式、外部链接式

### 行内样式

直接在标签的开始标签身上添加一个 **style=“”属性**，然后在引号里面书写css属性和属性值即可；

```html
<div style=“color:pink; font-size:16px;”>我是行内样式</div>
```

**注意：**没有实现结构和样式分离，尽量不用，后期不方便维护；

### 内部样式

书写在head标签里面，以一对**style标签**包裹

```html
<head>
    <meta charset="UTF-8">
    <meta http-equiv="X-UA-Compatible" content="IE=edge">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Document</title>
    <style>
        选择器 {
            属性: 属性值;
            属性：属性值
        }
    </style>
</head>
```

**注意：**实现了**结构和样式的半分离**，平时练习的时候可以用，实际开发中不推荐使用；

### 外部链接式（重点）

使用外部链接引入css使我们实际项目中常用的方法，我们需要通过两步操作完成：

第一步：在css文件夹中新建一个 **.css** 格式的css文件；

第二步：在html的head标签中用link引入，link标签需要配合相关的rel关系，type文件类型 （可以省略不写），href文件路径三个属性完成；

```
<link rel="stylesheet" href="./css/style.css">
```

**注意：**实现了**结构和样式的完全分离**，**代码；简洁，可读性强，实际开发中最常用**；

![](assets/03.png)



## 三、css语法规范（重点）

### 基本语法

```
        选择器 {
            属性1: 属性值;
            属性2: 属性值;
            ……
        }
```

**注意：**css属性和属性值之间要用英文冒号:连接，每一个属性和属性之间要用英文封号隔开（每一个属性需要用;结束）；

## 四、css选择器的作用

根据不同的需求选择不同的标签，设置对应的样式



## 五、基础选择器

![](assets/02.png)	

### 标签选择器（html选择器）

指用HTML标签名称作为选择器来选择元素设置样式。

按照标签名称分类，将页面中所有的当前标签选中指定统一的样式，比如以下代码：表示将当前页面中所有的p、div、li全部选中设置样式；

```css
        p {
            color: red;
        }

        div {
            color: aqua;
        }

        li {
            list-style: none;
        }
```

**注意：**标签选择器在实际开发中**不建议直接使用**，因为**会将页面中该标签全部选中，不能实现该标签的差异化设置**，**后期会配合后代选择器使用**；	

###  类选择器（重点）

**作用：**实际开发中我们可以通过类选择器给对应的标签设置名称，然后设置不同的样式，从而实现同一类标签的差异化设置；

实际开发中如果想要使用类选择器我们需要两步来完成：

第一步：在css文件中用英文点( **.** )后面紧跟着类名 称给元素设置对应的样式；

```css
 .类名称 { 
 	css属性:css属性值;
 }
```

第二步：在html结构中给对应的标签设置 **class属性="类名称"** ，调用css设置的样式；

```html
<div class="类名称"></div>
```

![](assets/04.png)

### id选择器

id选择器可以帮助我们设置标签样式，但是我们在实际开发中一般不会用id选择器设置布局样式。

id选择器在实际开发中我们主要是在javascript中获取元素使用：

```js
    <div id="box">老王</div>
    <script>
        // 获取id名称为box的盒子
        var box = document.getElementById('box')
        box.onclick = function () {
            alert('老王是最好的')
        }
    </script>
```

如果想要使用id选择器设置盒子样式，我们也要通过两步完成：

第一步：在css文件中用 **# 号** 后面紧跟着id名 称给元素设置对应的样式；

```css
 #id名称 { 
 	css属性:css属性值;
 }
```

第二步：在html结构中给对应的标签设置 **id属性="id名称"** ，调用css设置的样式；

```html
<div id="id名称"></div>
```

### 通配符选择器（同学们）*

一个 ***** 可以匹配当前页面的所有标签，设置统一的样式；

实际的开发中我们会设置所有标签的内外边距为0，放在css的最前面

```css
* {
     margin: 0;
     padding: 0;
   }
```



### 选择器命名规范

01、不能用纯数字、数字开头的、中文命名,可以用数字结尾；

02、命名最好有意义，尽量让别人一眼就能知道这个类名的目的，可以参照开发手册或者直接百度翻译即；

03、长名称或者词组可以使用横线或者下划线连接命名；

```html
    <div class="home-brick-box">可爱的程序员</div>
    <div class="home_brick_box">可爱的程序员</div>	
```

### 选择器使用注意事项和技巧（重点）

#### 类选择器使用注意事项 -- 重复使用性

类名称是可以重复调用的，前提条件是两个盒子样式完全一致；

#### 类选择高级技巧 -- 多类名调用

一个标签只能设置一个calss属性，如果想要调用多个类名我们可以在一个class里面直接以空格隔开直接书写另一个类名称即可；

```html
<!-- 语法： class="类名1 类名2 类名3 ..." -->
<div class="w box">可爱的程序员</div>
```

#### id选择器使用技巧 -- 唯一性

id选择器是唯一的不能重复使用，一个id名称一个页面只能出现一次；

## 六、元素的实体化三属性（重点）

所谓的实体化三属性指的就是元素的宽度width、高度height、背景background：

```css
        .box {
            width: 300px;
            height: 300px;
            background: red;
        }
```

**注意：**01、实体化三属性非常重要，只要书写的宽高都是和设计稿一样，静态页面就不会出现兼容问题；

​	    02、宽度和高度必须要加px像素单位；

## 七、常见文本控制属性（记住）

### 文字字体  font-family（ff）

设置文字显示的字体

```css
font-family: '宋体'; 
font-family: '宋体', Arial, 'Microsoft Yahei';
```

**注意：**01、字体的取值可以是一个值也可以是多个值，如果是**多个值需要用英文逗号隔开**，如果**字体是汉字或者多个英文单词组成可以用英文引号包裹起来**；

​	   02、谷歌浏览器默认的文字字体是微软雅黑；

### 文本大小font-size（fs）

设置文字字体大小，必须加px单位，其他单位（比如em、cm、mm）也可以但是我们常用px单位；

```css
 font-size: 30px;
```

### 文本粗细font-weight（fw）

html标签有一些标签默认有加粗效果（b、strong、h1-h6），有些没有加粗效果，我们可以通过font-weight来设置是否加粗；

**设置加粗样式**：font-weight取值为bold或者700

```css
   font-weight: bold;
   font-weight: 700;
```

**设置不加粗样式**：font-weight取值为normal或者400

```css
   font-weight: normal;
   font-weight: 400;
```

### 文本倾斜样式font-style （fs）

html标签i和em默认是倾斜样式，但是我们实际开发中很少出现倾斜的文字效果，如果使用i和em我们需要设置不倾斜，或者某些标签需要设置倾斜效果；

我们可以设置i和em不倾斜

```css
        i,
        em {
            font-style: normal;
        }
```

如果想要设置倾斜可以取值为italic

```css
 font-style: italic;
```

### 文本颜色color

设置文字的颜色显示，取值有三种：

01、预定义的英文（red，green，gold）；

02、十六进制取值，必须要用#号链接取值（#ffff00，#000，#f00);

03、rgb(颜色值1，颜色值2，颜色值3)   ----  ，rgb表示红绿蓝( rgb(red, green, blue))，取值为0-255的数字（黑色（0,0,0），白色rgb(255,255,255))；

```css
   /* 预定义英文 */
   color: red;
   /* 16进制取值 */
   color: #f00;
   /* rgb取值 */
   color: rgb(255, 0, 0);
```

### 行间距（行高）line-height  （lh）

设置两行文本之间的距离，也是一行文本的高度；

```css
line-height: 30px;
```

**注意：**如果**设置行高的时候不书写单位最终得到的行高大小是当前文字大小的倍数**，一般我们那会设置较小的倍数，当然我们推荐每一行的行高尽量按照设计稿的实际大小进行设置；

**测量行高的方法：**

**方法1：**从一行文本的开始到另一行文本开始或者从一行文本的结束到另一行文本的结束的高度；

![](assets/05.png)

**方法2：**UI设计师会给我们提前标注好，直接使用即可，如果没有标注就用方法1来测量即可；

### **单行文本垂直居中**（重点）

设置盒子的**行高等于盒子的高度就可以实现单行文本在盒子中垂直居中**；

![](assets/06.png)

```html
    <style>
        .loging {
            width: 180px;
            height: 40px;
            background-color: #4e6ef2;
            font-size: 18px;
            color: #fff;
            text-align: center;
            /*设置盒子的行高等于盒子的高度实现垂直居中*/
            line-height: 40px;
        }
    </style>
    <div class="loging">登录</div>
```

### 文本对齐text-align （ta）

设置一个盒子里面的文字对齐方式，默认取值为left，还有center和right取值；

```css
    line-height: 30px;
    /* 左对齐 */
    text-align: left;
    /* 居中对齐 tac */
    text-align: center;
    /* 居右对齐 */
    text-align: right;
```

**注意：**text-align不仅可以**让盒子里面**文字设置对齐方式，也可以给盒子里面的img、a、span、input、button等在一行显示多个的标签设置对齐方式；

![](assets/19.png)

### 文本缩进text-indent（ti）

网页的文章段落设置首行缩进两个文字的效果；

![](assets/07.png)

```css
    p {
        text-indent: 2em;
    }
```

**注意：**单位设置可以是px，也可以是em，em单位是一个相对单位，他是相对于当前文字的大小，1em=当前一个文字的大小（比如：文字font-size:30px;那么2em就相当于60px）；

### 文本线条text-decoration（td）

设置文字的下划线、上划线、删除线等样式

**取值有**：none、underline、overline、line-through

**none表示没有线**，一般超链接a浏览器默认会设置对应的下划线，我们可以通过none取值将a默认的下划线去除；

一般情况下我们会将以下代码放在css的最前面，表示将当前页面所有的a的默认下划线全部去除即可；

**没有线 tdn，一般设置在css的最前面，设置为超链接a，让页面中所有的a没有默认的下划线；**

```css
    a {
        text-decoration: none;
    }
```

**underline下划线（tdu）**，overline上划线（tdo），line-through删除线（tdl）

```css
    /* 下划线 tdu */
    text-decoration: underline;
    /* 上划线 tdo */
    text-decoration: overline;
    /* 删除线 tdl */
    text-decoration: line-through;
```

## 八、文本的综合写法font

实际开发中我们可以将**文字样式font-style、文字加粗font-weight、文字大小font-size、行高line-height，文字字体font-family进行合并书写**，达到简化代码的作用；

**基本语法：**

​    ***font*: font-style  font-weight  font-size/line-height  font-family;**

​    ***font*：是否倾斜 是否加粗 文字大小/行高 字体;**

```css
    /* 
    	font-size: 80px;
    	font-family: '微软雅黑';
    	line-height: 120px;
    	font-style: italic;
    	font-weight: 700; 
    */
    font: italic 700 80px/120px '微软雅黑';
```

**注意：**01、font的书写顺序是不能打乱的；
	     02、如果没有的属性可以省略不写，但是**文字大小和字体必须要存在，否则无效**；

## 九、谷歌浏览器调试

### 查看面板

在浏览器页面按下F12键或者右键检查可以调出控制台面板，点击左上角的小箭头，然后选择页面中需要查看的元素，左侧Elements是html结构，右侧styles可以查看该元素的样式；

![](assets/08.png)

### 常见的几个css错误

#### **01、样式被划掉**

![](assets/09.png)

**导致样式被划掉的原因有两个：**

**原因1：**是我们自己在css里面将该样式注释掉了

![](assets/10.png)

**原因2：**是该样式被重复设置了，当前的权重低于就近的样式

![](assets/11.png)

#### 02、出现黄色的感叹号

![](assets/12.png)

**原因1：**书写样式的时候使用标点符号用的时候中文的符号，鼠标放在黄色感叹号上直接会提示我们属性值value设置有问题；

![](assets/13.png)

**原因2**：书写样式属性名称出现单词错误，鼠标放在黄色感叹号上直接会提示我们属性name设置有问题；；

![](assets/14.png)

**注意：以上两种原因我们都可以用鼠标经过黄色感叹号按照弹出的提示判断问题原因；**

## 十、案例和作业

### 案例

#### 新闻详情页

![](assets/15.png)

#### 小米产品案例

![](assets/16.png)

### 作业：

#### 百度搜索

![](assets/17.png)

#### 新闻详情页

![](assets/zy.jpg)

#### 百度首页（选做）

![](assets/18.png)






















































































































































































































































































































































































































































































































































































































































































































































































































































































































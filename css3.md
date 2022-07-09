## 一、css三大特性

### 01、层叠性（覆盖性）

一个标签的同一个属性被多次重复设置，最后设置的一次会生效，其他的都会被层叠覆盖；

遵循了**就近原则**；

```css
    .box {
        width: 300px;
        height: 300px;
        background-color: royalblue;
        width: 100px;
    }
```

以上代码盒子的宽度最终大小为100px，将最前面的300px覆盖掉了；

### 02、继承性

有一些css属性子级元素或继承父级元素的样式，不需要单独设置，控制文字的相关属性（text-，font-，line-，color）几乎都可以被继承；

***注意：01、超链接a元素不会继承父级盒子的color颜色，因为浏览器默认给a设置默认的颜色样式，我们需要单独设置a的color颜色；*****

![](C:/Users/lenovo/Desktop/%E5%9F%BA%E7%A1%80%20%E8%B5%84%E6%96%99%2012/css%E7%AC%AC%E4%B8%89%E5%A4%A9/%E4%B8%8A%E8%AF%BE%E7%AC%94%E8%AE%B0/assets/01.png)

**02、标题标签h1,h2,h3,h5,h6不会直接继承父级盒子的文字大小font-size，因为他们本身自己有默认的文字大小并且是em相对单位，我们得到的结果是我们设置父级文字大小乘以这个倍数；所以我们需要单独设置；**

![](C:/Users/lenovo/Desktop/%E5%9F%BA%E7%A1%80%20%E8%B5%84%E6%96%99%2012/css%E7%AC%AC%E4%B8%89%E5%A4%A9/%E4%B8%8A%E8%AF%BE%E7%AC%94%E8%AE%B0/assets/02.png)

### 03、权重优先级

不同的选择选择元素的时候权重大小不同，我们以基础选择器为参照，计算出我们自己选择器权重大小；

#### 基本计算

01、继承性是没有权重的，如果当前元素自己有样式，就不会继承父级的样式，所以**继承性的权重为0**；

02、标签选择器，伪元素，的权重为1 （0,0,0,1）

03、类选择器，伪类选择器，属性选择器的权重为10    （0,0,1,0）

04、id选择器的权重为100    （0,1,0,0）

05、行内样式的权重为1000   （1,0,0,0）

06、可以给样式设置!important  提高权重 ，权重是无限大；

#### 权重叠加

实际开发中我们往往是按照复合选择器书写样式，所以我们就会将一些权重进行叠加计算,比如以下代码就可以计算出不同的权重值；

```CSS
     .box li a {
         color: red;
     }
     .box li a:hover {
        color: salmon;
     }
```

 .box li a  的权重值 = 0,0,1,0 + 0,0,0,1 + 0,0,0,1 = 0,0,1,2 = 12

.box li a:hover的权重值 =  0,0,1,0 + 0,0,0,1 + 0,0,0,1 + 0,0,1,0 = 0,0,2,2 = 22

**注意**:**权重叠加是不会有进位的**，每一类基础选择器只能在自己的位置叠加，如果超过10也不能向前进位哦；相当于现实辈分和年龄是不能对比的；

#### 课堂练习

6道精华题

## 二、盒子模型（重点）

### 网页布局本质

所谓的网页布局就是利用 CSS 摆放盒子，我们需要设置盒子的占位大小，设置盒子不同的摆放位置；

### 盒子模型的组成部分

一个完整的布局盒子主要包括内容content，边框border，外边距margin，内边距padding；

#### 内容content

我们自己设置的宽高或者盒子默认的宽高；

#### 边框border

##### 边框三要素

盒子的边框设置，border是有三个要素组成的：**边框样式border-style，边框粗细border-width，边框颜色border-color**

```css
    border-style: solid;
    border-width: 2px;
    border-color: red;
```

**注意**：边框样式border-style取值常见的有**实线solid，虚线dashed，点线dotted**；

##### border的综合写法

**语法：*border*: 线条样式   线条粗细  线条颜色;**

```css
    /* 
	border-style: solid;
    border-width: 2px;
    border-color: red; 
	*/
    border: solid 2px red;
```

##### 设置不同方向的边框

**语法：border-方位名词：线条样式   线条粗细  线条颜色；**

```css
    border-top: solid 2px red;
    border-bottom: solid 2px red;
    border-left: solid 2px red;
    border-right: solid 2px red;
```

##### 设置单独某个方向的某个属性

**语法：border-方位名词-属性：属性值；**

```css
    border-left-color: red;
    border-right-style: solid;
    border-top-width: 3px;
```

#### 外边距margin

**作用：**设置两个盒子之间的距离；

![](C:/Users/lenovo/Desktop/%E5%9F%BA%E7%A1%80%20%E8%B5%84%E6%96%99%2012/css%E7%AC%AC%E4%B8%89%E5%A4%A9/%E4%B8%8A%E8%AF%BE%E7%AC%94%E8%AE%B0/assets/04.png)

##### 设置不同方向的内边距

**语法：margin-方位名词：值；**

```css
    margin-left: 20px;
    margin-right: 20px;
    margin-top: 20px;
    margin-bottom: 20px;
```

##### 取值个数不同

取值为1个值表示四个方向都一致；

```css
margin: 20px;
```

取值为2个值表示： **上下   左右**；

```css
margin: 20px  30px;

```

取值为3个值：**上   左右  下**；

```
margin: 20px  10px  5px;

```

取值为4个值：**上  右   下  左；**

```
margin: 20px  30px  8px 80px;

```

#### 内边距padding

**作用：**设置内容距离盒子边缘的距离；

![](C:/Users/lenovo/Desktop/%E5%9F%BA%E7%A1%80%20%E8%B5%84%E6%96%99%2012/css%E7%AC%AC%E4%B8%89%E5%A4%A9/%E4%B8%8A%E8%AF%BE%E7%AC%94%E8%AE%B0/assets/03.png)

##### 设置不同方向的内边距

**语法：padding-方位名词**

```css
    padding-left: 20px;
    padding-right: 20px;
    padding-top: 20px;
    padding-bottom: 20px;

```

##### 取值个数不同

取值为1个值表示四个方向都一致；

```css
padding: 20px;

```

取值为2个值表示： **上下   左右**；

```css
padding: 20px  30px;

```

取值为3个值：**上   左右  下**；

```
padding: 20px  10px  5px;

```

取值为4个值：**上  右   下  左；**

```
padding: 20px  30px  8px 80px;

```

## 三、盒子模型相关布局问题以及技巧（重点）

### 01、盒子的实际占位大小计算

盒子的实际占位大小指的就是我们设置好宽高的基础上累加padding和border的大小；

**盒子的实际宽度  = width + 左右的padding + 左右的border；**

**盒子的实际高度  = height+ 上下的padding + 上下的border；**

![](C:/Users/lenovo/Desktop/%E5%9F%BA%E7%A1%80%20%E8%B5%84%E6%96%99%2012/css%E7%AC%AC%E4%B8%89%E5%A4%A9/%E4%B8%8A%E8%AF%BE%E7%AC%94%E8%AE%B0/assets/05.png)

### 02、padding和border撑大盒子问题

如果盒子宽高设置固定了，再去给盒子添加padding和border就会将盒子的大小撑大；

#### **解决方案1：人为手动加多少减多少**：

加多少减多少，将我们自己设置的宽高减去对应的padding和border即可；

![](C:/Users/lenovo/Desktop/%E5%9F%BA%E7%A1%80%20%E8%B5%84%E6%96%99%2012/css%E7%AC%AC%E4%B8%89%E5%A4%A9/%E4%B8%8A%E8%AF%BE%E7%AC%94%E8%AE%B0/assets/07.png)

#### 解决方案2：开启css3的盒子内减模式

直接给盒子设置css3的内减模式 **box-sizing: border-box;**

浏览器在解析的时候就会自己算我们的尺寸，会将设置的padding和border全部减去然后重新计算盒子的大小；

![](C:/Users/lenovo/Desktop/%E5%9F%BA%E7%A1%80%20%E8%B5%84%E6%96%99%2012/css%E7%AC%AC%E4%B8%89%E5%A4%A9/%E4%B8%8A%E8%AF%BE%E7%AC%94%E8%AE%B0/assets/06.png)

### 03、外边距塌陷问题（了解）

#### 情况1：上下排列的盒子外边距合并

上下排列的两个盒子，上面的盒子设置了marin-bottom,下面的盒子设置了margin-top，最终显示的样式两个值谁大就显示谁，小的值被大的值合并了；

**解决方案**：单独设置给其中某一个盒子，不要两者都设置；

#### 情况2：嵌套盒子外边塌陷（外边距穿透）

如果两个盒子有嵌套包含的父子级关系，如果给子级盒子设置了margin-top，效果显示父级盒子也会跟着掉下来；

![](C:/Users/lenovo/Desktop/%E5%9F%BA%E7%A1%80%20%E8%B5%84%E6%96%99%2012/css%E7%AC%AC%E4%B8%89%E5%A4%A9/%E4%B8%8A%E8%AF%BE%E7%AC%94%E8%AE%B0/assets/04.jpg)

**解决方案1：**给父级盒子设置边框border，推荐只设置border-top，如果父盒子本身就有border就不会出现塌陷问题；

**解决方案2：**给父级盒子设置内边距padding，推荐只设置padding-top，如果父盒子本身就有padding就不会出现塌陷问题；

**解决方案3：**给父级盒子设置overflow:hidden；、display:flow-root；利用盒子的BFC模式；

**解决方案4：**如果父级盒子或者子级盒子有了浮动或者定位就不会出现塌陷；

### 04、外边距的经典应用：设置盒子水平居中

想要使用**margin:0 auto;**设置一个盒子居中必须满足两个条件：

01、盒子必须是块元素，独自占一行；

02、盒子必须要有固定的宽度；

**注意：实际开发中最常用就是设置版心盒子居中；**

**版心：**网页的主体内容显示的区域，一般是一个固定宽度的盒子，在浏览器的中心显示；版心的类名一般用w或者container表示；目前市场的版心一般都在1200左右（传智1200，京东1190、小米1226）；

**实际的开发中版心是不需要固定的高度的，因为每一个模块的高度不一样；**

```css
        .w {
            width: 1200px;
            margin: 0 auto;
            background-color: red;
        }

```

![](C:/Users/lenovo/Desktop/%E5%9F%BA%E7%A1%80%20%E8%B5%84%E6%96%99%2012/css%E7%AC%AC%E4%B8%89%E5%A4%A9/%E4%B8%8A%E8%AF%BE%E7%AC%94%E8%AE%B0/assets/08.png)

### 004、行内元素和行内块元素居中text-align：center；

将行内元素和行内块元素放在一个父级盒子中，设置父级盒子tac即text-align：center；就可以居中

### 05、清除内外边距

有些html标签浏览器在解析的时候回有默认的内边距padding或者外边居marign，我们需要将默认的样式清除，再去设置自己的样式；

比如：body有8px的默认外边距，ul有默认的内边距等

我们只需在css的最前面将所有标签的margin和padding清0即可；

```css
    * {
        margin: 0;
        padding: 0;
    }

```

### 06、细线表格（边框合并）--- 死了都要记

实际工作我们经常使用表格展示数据，我们用css设置细线表格，我们只需要给table、th、td标签同时设置边框border，然后设置边框合并属性*border-collapse*: collapse;即可实现；

```css
        table,
        th,
        td {
            border: 1px solid #ccc;
            border-collapse: collapse;
        }

```

![](C:/Users/lenovo/Desktop/%E5%9F%BA%E7%A1%80%20%E8%B5%84%E6%96%99%2012/css%E7%AC%AC%E4%B8%89%E5%A4%A9/%E4%B8%8A%E8%AF%BE%E7%AC%94%E8%AE%B0/assets/20.png)

### 07、border书写三角形效果（了解）

![](C:/Users/lenovo/Desktop/%E5%9F%BA%E7%A1%80%20%E8%B5%84%E6%96%99%2012/css%E7%AC%AC%E4%B8%89%E5%A4%A9/%E4%B8%8A%E8%AF%BE%E7%AC%94%E8%AE%B0/assets/21.png)

盒子宽高必须都是0，然后设置盒子四条边都是透明，最后单独设置一个方向的边的颜色即可；

```css
    width: 0;
    height: 0;
    border: 20px solid transparent;
    border-top-color: red;

```

## 四、css3常用新属性

### **圆角*border-radius***

#### 圆角矩形

*border-radius*取值为一个实际像素

```css
        .box {
            width: 300px;
            height: 100px;
            background-color: #f00;
            border-radius: 15px;
        }

```

![](C:/Users/lenovo/Desktop/%E5%9F%BA%E7%A1%80%20%E8%B5%84%E6%96%99%2012/css%E7%AC%AC%E4%B8%89%E5%A4%A9/%E4%B8%8A%E8%AF%BE%E7%AC%94%E8%AE%B0/assets/14.png)

#### 圆形

矩形必须是正方形，设置border-radius*取值大于等于高度一半或者直接设置50%

```css
        .box {
            width: 100px;
            height: 100px;
            background-color: #f00;
            /* border-radius: 50px; */
            border-radius: 50%;
        }

```

![](C:/Users/lenovo/Desktop/%E5%9F%BA%E7%A1%80%20%E8%B5%84%E6%96%99%2012/css%E7%AC%AC%E4%B8%89%E5%A4%A9/%E4%B8%8A%E8%AF%BE%E7%AC%94%E8%AE%B0/assets/15.png)

#### 胶囊形状

矩形必须是长方形，设置border-radius*取值大于等于高度一半；

![](C:/Users/lenovo/Desktop/%E5%9F%BA%E7%A1%80%20%E8%B5%84%E6%96%99%2012/css%E7%AC%AC%E4%B8%89%E5%A4%A9/%E4%B8%8A%E8%AF%BE%E7%AC%94%E8%AE%B0/assets/16.png)

```css
        .box {
            width: 300px;
            height: 50px;
            background-color: #f00;
            border-radius: 25px;
        }

```

如果设置border-radius*取值为50%，会绘制椭圆

![](C:/Users/lenovo/Desktop/%E5%9F%BA%E7%A1%80%20%E8%B5%84%E6%96%99%2012/css%E7%AC%AC%E4%B8%89%E5%A4%A9/%E4%B8%8A%E8%AF%BE%E7%AC%94%E8%AE%B0/assets/17.png)

```
        .box {
            width: 300px;
            height: 50px;
            background-color: #f00;
            border-radius: 50%;
        }

```

#### 半圆

设置border-radius*取值个数为4个值：分别是：**左上角  右上角  右下角 左下角**

语法：**border-radius：左上角  右上角  右下角 左下角；**

```
        .box {
            width: 100px;
            height: 100px;
            background-color: #f00;
            border-radius: 0 50px 50px 0;
        }

        .box1 {
            width: 100px;
            height: 100px;
            background-color: #f00;
            border-radius: 50px 0 0 50px;
        }

```

![](C:/Users/lenovo/Desktop/%E5%9F%BA%E7%A1%80%20%E8%B5%84%E6%96%99%2012/css%E7%AC%AC%E4%B8%89%E5%A4%A9/%E4%B8%8A%E8%AF%BE%E7%AC%94%E8%AE%B0/assets/18.png)

### 盒子阴影box-shadow

**语法**

```
box-shadow: h-shadow v-shadow blur spread color inset;
box-shadow:水平阴影   垂直阴影   模糊距离   阴影大小   阴影颜色  内/外阴影；

```

**水平阴影：**   阴影在盒子的水平方向左右的位置设置；
**垂直阴影：**   阴影在盒子的垂直方向上下的位置设置；
**模糊距离：**   阴影的羽化模糊的程度，值越大越模糊；
**阴影大小：**   设置阴影的大小尺寸，一般可以不设置，有了需求在设置；
**阴影颜色： **  阴影的颜色显示；
**内/ 外阴影：**阴影在盒子的内部显示还是外部显示，默认不设置是外部阴影，想要设置内阴影就设置取值为inset；

**注意：一个盒子可以加多个阴影，用个英文的逗号隔开即可**

```css
box-shadow: 5px 5px 10px #000, 20px 20px 10px red;

```

### 文字阴影	

**语法**

```
	text-shadow: h-shadow v-shadow blur color;
	text-shadow:水平阴影   垂直阴影   模糊距离   阴影颜色 ；

```

参数和盒子阴影差不多；

**案例：实现凹凸文字效果：**

![](C:/Users/lenovo/Desktop/%E5%9F%BA%E7%A1%80%20%E8%B5%84%E6%96%99%2012/css%E7%AC%AC%E4%B8%89%E5%A4%A9/%E4%B8%8A%E8%AF%BE%E7%AC%94%E8%AE%B0/assets/19.png)

## 五、光标类型cursor（了解）

默认的小箭头 

```css
cursor: default;

```

小手形状

```css
cursor:pointer;

```

移动图标

```css
cursor:move;

```

文本图标

```css
cursor:text;

```

禁止点击图标

```css
cursor:not-allowed;		

```

## 六、css3过渡动画（死了都要记） 

**语法：transition: 属性   时间  运动曲线 延时;**

> ```
> 属性：需要改变过渡的属性
> 时间：整个过度动画需要多长时间完成
> 运动曲线 ：动画运动形式默认取值为ease。匀速运动linear；
> 延时：鼠标移入需要等待一段时间再去加载过渡动画；
> 
> ```

**实际开发中一般只会调用属性和时间**

```
transition: 属性   时间；

```

> **注意：**
> 01、同时修改多个属性，需要用英文逗号隔开
> 	transition: width 1s, background-color 1s, height 1s;
> 02，**用逗号隔开书写多个属性过渡太麻烦，我们只需要用一个all表示所有的属性即可**
> 	**transition: all 1s ；**
> 03、**过渡加在本身上，谁做动画给谁加；**






















































































































































































## 一、列表

### 列表的应用场景

网页布局的时候离不开列表的使用，我们可以使用列表完成，如新闻列表、网站导航、图文卡片、网站底部导航等；

![](assets/01.png)

### 列表的分类

列表主要分为无序列表、有序列表、自定义列表；

#### 无序列表(重点)

**基本结结构：**一个ul表示列表的整体，里面嵌套多个li标签；

```html
    <ul>
        <li></li>
        <li></li>
        <li></li>
    </ul>
```

**注意：**01、ul里面只能嵌套li，li里面可以嵌套任何的标签内容；

​	   02、无序列表里面的列表项li是没有先后的顺序的；

​	   **03、实际开发中我们使用无序列表，最好在外面嵌套一个div，方便控制样式；**

​           04、li默认的有样式后期学习css的时候回去除；

#### 有序列表

**基本结结构：**一个ol表示列表的整体，里面嵌套多个li标签；

```html
    <ol>
        <li></li>
        <li></li>
        <li></li>
    </ol>
```

**注意：**ol里面只能嵌套li，li里面可以嵌套任何的标签内容；

#### 自定义列表

**基本结结构：**一个dl表示列表的整体，里面嵌套一个dt和多个dd，dt表示描述标题，dd表示描述内容；

```html
    <dl>
        <dt></dt>
        <dd></dd>
        <dd></dd>
        <dd></dd>
    </dl>
```

**注意：**dl里面只能嵌套dt和dd，dt和dd里面可以嵌套任何的标签内容；

## 二、表单

### 作用：

收集用户信息；

![](assets/02.png)

### 表单的组成

一个完整的表单是由提示文本、表单域（form）、表单控件三部分组成的；

![](assets/03.png)

#### 提示文本

提示用户需要填写的相关信息的说明文字；

#### 表单域（form）

将收集的用户信息提交到后台服务器保存使用，所有的**提示文本和表单控件都要放在form表单域中**；

```html
 <form action="" method=""   name=“”></form>
```

form表单域有三个常见的属性action、method、name；

**action：**设置要提交的地址，将收集的数据提交到指定的地址；

**method：**提交数据的方式，有post和get两种，post属于加密提交，get属于明文提交（不需要加密直接提交）；

**name：**区分数据的分类，给对应的数设置名称；

#### 表单控件

表单控件主要有input表单控件、select下拉列表、textarea文本域等；

##### input表单控件

```html
<input type="">
```

我们可以通过设置input表单不同的type取值实现不同表单功能；

###### 文本框  type取值为text

```html
<input type="text" >
```

###### 密码框   type的取值为password

```html
<input type="password" >
```

###### 单选框   type的取值为radio

```html
<input type="radio"  name="sex" >  男
<input type="radio"  name="sex" >  女
```

**注意：**想要实现单选效果，必须要设置相同的name属性，name属性的取值是自己定义的；

###### 复选框  type的取值为checkbox

```html
<input type="checkbox"  >  跑步
<input type="checkbox"  >  写代码
```

注意：复选按钮设置了相同的name不会影响复选功能；

###### 提交按钮  type取值为submit

```html
<input type="submit"  >
<input type="submit"  value="提交数据" >
```

**注意：**提交按钮默认有 “提交” 文字，我们也可以用value属性设置自己的文字；

###### 重置按钮  type的取值为reset

```html
<input type="reset"  >
<input type="reset"  value="重新填写" >
```

**注意：**重置按钮默认有 “重置” 文字，我们也可以用value属性设置自己的文字；

###### 普通按钮  type的取值为button

```html
<input type="button"  value="注册" >
```

**注意：**普通按钮没有默认文字，需要使用value属性设置文字，普通按钮没有任何功能，后期用js绑定相关功能；

###### 图片按钮  type的取值为image

图片按钮可以按钮的样式更加美观，同样具有数据提交的功能；

```html
<input type="image" src="图片路径"  alt="" >
```

**注意：**图片按钮必须要配合src属性获取对应的图片按钮路径，否则显示找不到图片；

###### 双标签button按钮（常用）

双标签button也是按钮样式，同样具有提交数据的功能；

```html
<button>按钮</button>
```

###### 文件域  type取值为file

文件域file有提交文件的功能，但是该控件目前只能上传一个文件，H5可以设置multiple属性实现上传多个文件的功能；

```html
<input type="file" >
<input type="file"  multiple="multiple">
```



##### select下拉列表

我们可以通过下拉列表将对应的参数选项折叠起来，方便我们调用，节约布局空间；

基本结构：

一对select标签嵌套多个option标签；

```html
    <select name="" >
        <option value=""></option>
        <option value=""></option>
        <option value=""></option>
    </select>
```

**注意：**如果想要默认选中其中某一项，需要给对应option设置selected=“selected”表示默认选中；



##### textarea文本域

用于定义多行的文本输入控件。该控件中可以容纳无限数量的文本。我们可以通过cols和rows属性来规定textarea的尺寸。

```html
<textarea cols="30" rows="10"></textarea>
```

**注意**：cols和rows控制文本域的输入行数和每行输入的文字个数，**实际开发中不建议使用，后期用css控制**；

**设置默认值的方法有两种**: 

```html
    <textarea cols="30" rows="10">默认值</textarea>
    <textarea cols="30" rows="10" placeholder="默认值"></textarea>
```

01、直接在尖括号之间书写默认文字即可，但是不能敲任何回车或空格需要紧贴着书写；

02、placeholder设置默认值；

### 常见的表单属性

#### name属性

作用：给数据设置名称，区分数据的类别

#### checked属性

取值为自己，设置单选和复选按钮默认选中效果；

```html
	<input type="checkbox" checked="checked" >
	<input type="checkbox" checked>
```

注意：属性和属性值一致，可以直接省略属性值

#### value属性

设置修改**表单的默认值**，一般是用来获取值使用；

后期咱们用来获取表单的数据，**一般设置为空**，用户输入以后才能获取；

建议设置为空

```html
<input type="text"  value="">
```

#### maxlength最大长度

限制最多输入的内容长度，取值是阿拉伯数字

```html
<input type="text" maxlength="3">
```

#### placeholder属性

css3新增的占位符，只有提示作用，不能获取值

```html
<input type="text" placeholder="占位符">
```

*注意：如果表单设置了value的默认值，那么占位符placeholder无效；*

### label用户体验提升设置

提高用户操作表单控件的体验，通常和对应的input功能控件关联使用；

label有一个常用的属性for，我们可以在对应的input控件设置id属性并且设置id值，然后用label嵌套对应的提示文本，设置label的取值为id的值即可实现点击提示文本直接获取对应input控件的焦点；理解为以下步骤：

**第一步：在input控件上设置id="id值"；**

**第二步：用label标签嵌套提示文本，然后设置label的for属性取值为id的值；**

```html
    <label for="user">用户名</label> <input type="text" id="user">
    <label for="nan">男</label> <input type="radio" id="nan">
    <label for="nv">男</label> <input type="radio" id="nv">
```
























































































































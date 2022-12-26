# 第一章HTML基础

## HTML基本结构

**一个完整的HTML文档至少要包含**:`html`，`head`，`tltle`,`body`这4标签。成对出现

~~~html
<!DOCTYPE html> <!--表示文档的类型。 document type-->
<html><!--根标签-->
    <head>
        <title>标题名</title><!--可以定义标签名-->
    </head>
    <body>
        主体
    </body>
</html>
~~~

* **`<html>`**：根标签，页面所有内容都必须包含`<html>`和`</html>`之间。
* **`<head>`**：定义**html**文档的头部分，包含页面**标题、样式、脚本**等。
* **`<body>`**：定义了主体部分，呈现给用户览的内容
* **`<meta>`**：描述网页的具体摘要信息。描述的内容并不显示在浏览器的窗口中。目的是方便浏览器 解析或者利用搜索引擎进行搜索。

### 注释

```html
<!--注释--> 或快捷键 ctrl
```



## 常用标签

### 标题标签

**`<h1>~<h6>`**：设置网页中的标题文字，总共6级。

~~~html
<h1>
    标题
</h1>
~~~

### 段落标签

**`<p>`**：表示以段落的形式组织内容

### 换行标签

**`<br/>`**：表标强制换行显示，这个标签没有结束标签，自闭合

### 格式化标签

#### 居中标签

**`<center>`**：用于将页面元素在所处父标签中居中显示

#### 有序无序列表标签

**`<ol>`和`<ul>`**：分别是**有序**，和**无序**列表 。**`<li>`**是列表项。

~~~html
<!--有序-->
<ol>
    <il>序列一</il>
    <il>序列二</il>
    <il>序列三</il>
</ol>
<!--无序-->
<ul>
    <il>序列一</il>
    <il>序列二</il>
    <il>序列三</il>
</ul>
~~~

#### 标记文本的增删

**`<del>`和`<ins>`**：分别是**删除线**和**下划线**

~~~html
<del>删除线</del>
<ins>下划线</ins>
~~~

#### 预定义标签

**`<pre>`**：可以设置某种自定义的格式。

### 字体标签

**`<font>`**:用于设置字体的字号、颜色等。

~~~html
<font size="7" color="red">字体</font>
~~~

**font**

> * **`size`**：设置字体大小。取值范围1~7、默认字体大小为3。
>
> * **`color`**：设置字体颜色。

### 图像标签

**`<img>`**：用于在网页中插入图像，**自闭合**。图片格式有jpg、png、gif等。

~~~html
<img src="路径\图片名.jpg" align="left" title="图片标题" width="80px" height="100px"/>
<!-- px单位像素
~~~

**img**

> * **`src`**：图片路径，也可以输入图片名，但必须是当前路径
> * **`width`和`height`**：设置图片的宽和高
> * **`title`**：图片的标题
> * **`align`**：对齐方式。
>   * **right**：右对齐
>   * **left**：左对齐
>   * **middle**：中央对齐

### 超链接标签

**`<a>`**：用于创建超连接。

~~~html
<a href="https://www.baidu.com">网址</a>
~~~

**a**

> **`href`**：输入网址

# 第二章表格和表单

## 表格

### 表格的基本语法

**分别有:`<table>`、`<tr>`、`<td>`、`<th>`、`<caption>`**

```html
<table><!--表格开始-->
    <caption>表格标题</caption>
    <tr>
        <th>单元格</th><!--默认发居中加粗-->
           ...
    </tr>
    <tr><!--行开始-->
        <td>单元格</td>
           ...
    </tr><!--行结束-->
</table><!--表格结束-->
```

**table**

> **`<table>`**：`table`是表格的是外层标记，一个表格从`<table>`开始到`</table>`结束
>
> **`<caption>`**：在`<caption>`标记中的文字就作为表格标题，通常会居中显示的表格上方。`<caption>`标记必须直接放置到`<table>`标记之后，每个表格只能设置一个标题。
>
> **`<tr>`**：网页的表格是按照行画的。每出一对`<tr></tr>`表示一行。`<tr>`上级的父标记是`<table>`
>
> **`<th>`**：`<th>`和`<td>`表示的都是单元格，但`<th>`中内容默认是居中并以粗体显示。`<th>` 经常用于表头的单元格
>
> **`<td>`**：`<td>`元素表示表格中的数据，`<td>`到`</td>`表行是的一个单元格。`<td>`中的内容就是单元格的内容。`<td>`的上一级父标记是`<tr>`。内容也可以是图片

### 表格的属性

#### table边框属性

**`border`**：表示是否是显示表格的边框，只使用“1”或“0”; ”0“表示没有边框，默认不为”0“。”1“表示为边框。

```html
<table border="属性值">
```

### 合并单元格

> 可以通过**`<colspan>`**和**`<rowspan`**属性让`<th>`或`<td>`跨越一个以上的列或行。对该属性指定的数值表标的是跨越的单元格的数量。

#### 列合并和行合并

```html
<table><!--表格的开始-->
    <caption>标题</caption>
    <tr><!--一行的开始-->
        <th colspan="3">占三列</th> <!--列合并-->
    </tr><!--一行的结束-->
    <tr> 
        <td>1</td>
        <td>2</td>
        <td>3</td>
        <td rowspen="2">行合并</td>
    </tr>
</table><!--表格的结束-->
```

`<th>`和`<td>`

> **`colspan`**：列合并
>
> **`rowspan`**：行合并

### 表格按行分组显示

**`<thead>`**、**`<tfoot>`**、**`<tbody>`**元素使你有能力对表格中的行进行分组

* **`<tfoot>`**：标记定义表格的页脚(脚注或表注)。该标记用于组合 HTML 表格中的表注内容。  元素应该与`<thead>`和`<tbody>`元素结合起来使用。
* **`<thead>`**：元素用于对 HTML 表格中的表头内容进行分组
* **`<tbody>`**：用于对 HTML 表格中的主体内容进 行分组。 在默认情况下这些元素不会影响到表格的布局。

```Html
<!DOCTYPE HTML>
<html>
<head>
	<title>表格的分组</title>
</head>
<body>
	<table border="1">
		<thead>
			<tr>
				<th>月份</th>
				<th>收入（￥）</th>
			</tr>
		</thead>
		<tfoot>
			<tr>
				<td>总计</td>
				<td>5800</td>
			</tr>
		</tfoot>
		<tbody>
		<tr>
			<td>一月</td>
			<td>1800</td>
		</tr>
		<tr>
			<td>二月</td>
			<td>2000</td>
		</tr>
		<tr>
			<td>三月</td>
			<td>2000</td>
		</tr>
		</tbody>
    </table>
</body>
</html>
```

## 表单

### 表单基体结构

表单是与**用户交互信息**的主要手段。比如常用的**用户注册**、**在线联系**、**在线调查表**等都是表单的具全应用形式。

~~~html
<form name="表单名称" method="定义表单的提交方式" action="服务器地址" >
    ……
    表单元素(如文本框、单选按钮、复选框、文本区域等)
    ……
</form>
~~~

**form**属性

> **`name`**：表示表单的名称
>
> **`method`**：用来定义提交信息的方式，取值为**post**和**get**,默认为**get**
>
> **`action`**：用来指定指定处理数据的程序文件所在的位置，单击提交按钮后，就将表单信息提交给文件进行处理。

### 表单基本元素

表单重要的两个组成部分**表单域**和**表单按钮**。

* **表单域**：文本框、密码框、隐藏域、多行文本框、复选框、单选框、下拉选择、文件上传框。
* **表单按钮**：提交按钮、复位按钮、一般按钮。

### `<input>`元素

该标记可以在表单中定义**单行文本框**、**单选按钮**、**复选框**等表单元素。

#### `<input>` 基本语法

```html
<input name="表单元素名" type="定义属性">
```

##### `<input>`元素说明

| 属性     | 功能                                                         |
| -------- | ------------------------------------------------------------ |
| type     | 插入表单的元素类型                                           |
| neme     | 表单元素的名称                                               |
| size     | 单行文本框的长，取值为数字，表示多少个字符长                 |
| maxlegth | 单行文本框可以输入的最大字符数，取值数字，表示多少个字符，当大于size的属性值时，用户可以移动光标来查看整个输入的内容。 |
| value    | 对于单行文本框，表示输入文本框的默认值，可选属性对于单选按钮或复选框，则指定单选 按钮被选中后传送到服务器的实际值，必选属性。对于按钮，则指定按钮表面上的文本，可选。 |
| checked  | 若被加入，则默认选中。                                       |
| radonly  | 表单为只读                                                   |

###### `type`插入的类型

| 属性值   | 说明                                                         |
| -------- | ------------------------------------------------------------ |
| text     | 表示单行文本框                                               |
| password | 表示密码框                                                   |
| radio    | 单选按钮                                                     |
| checkbox | 表示复选框                                                   |
| submit   | 表示提交按钮                                                 |
| reset    | 表示重置按钮                                                 |
| button   | 表示创建一个按钮，该按钮的具体功能。需要另外编程             |
| image    | 表示图像域，此时input标记还有一个重要属性：src，用来指定图像域的来源 |
| file     | 表示文件域                                                   |
| hidden   | 隐藏文本框域，类似于text，但不可见，常用传递信息。           |
| number   | 数字                                                         |

### 表单元素操作

#### 文本框和密码框

**基本语法**

~~~html
<input type="类型" name="名称" readonly="只读" size="宽度" maxlength="可输入字符数" value="默认值">
~~~

> **size**：表示当前单元框的长度
>
> **maxlength**：表示当前单元框能输入字符的长度

#### 按钮

表单常用的按钮有四种：**提交按钮**、**重置按钮**、 **普通按钮**、**图片按钮**。

* **提交按钮**：**`submit`**
* **重置按钮**：**`reset`**重置按钮就是让所有表单数据都还原到初始值。
* **普通按钮**：**`button`**普通按钮就是能生成一个按钮的形状，但单击按钮不会有任何操作，需要配合相关代码支持功能操作。
* **图片按钮**：图片按钮当 `input`标记的属性值为`image`时，就成为一个图像域，图像域相当于一个图片样式的提交按钮。

~~~html
<html>
    <head>
        <title>按钮</title>
    </head>
    <body>
        <form>
            
            用户名:<input type="text" name="uname" value="Mary" />
            <br /> <br />
            密码:<input type="password" name="upass" />
            <br /> <br />
            年龄:<input type="text" name="uage" size="2" maxlength="3" />
            <br /> <br />
            <input type="submit" value="提交按钮" />
            <input type="reset" value="重置按钮" />
            <input type="button" value="普通按钮" onClick="window.alert('请输入用户信息')" />
            <input type="image" src="图片名" width="宽度" height="高度" />
        </form>
    </body>
</html>
~~~

#### 单选按钮

~~~html
<form>
    性别:
    <input type="radio" name="sex" value="男" checked="checked"/>男生
    <input type="radio" name="sex" value="女" />
</form>
<!--
radio 表示单选按钮 名字必须相等
checked 表示默认选择项
~~~

#### 复选框

复选框允许从一个选项列表中选择多个选项。在 input 标记中设置 type 属性值为 **checkbox** 。在定义选项时，要 注意如果 name 值一样的话，用户所有选项会组合为一个数据进行提交。、

~~~html
<form>
    个人爱好<br /> <br />
    <input type="checkbox" name="1" value="跳" />跳舞
    <input type="checkbox" name="1" value="唱" />唱
    <input type="checkbox" name="1" value="篮球" />篮球
</form>
~~~

#### 文件域

文件域类型用于文件上传。在设计网站时，有时会需要用户上传一些本地计算机上的一些文件。这时候使用文件域 就会非常方便，可以让用户自行选择要上传的文件。

```html
<form>
    <input type="file" name="文件" />
</form>
```

#### hidden类型

hidden类型可以定义一个隐藏的表单控件。在浏览器中，这个隐藏项用户是看不到的。通常情况下，设计者可以 利用隐藏表单控件存储一些数据，可以当作一个页面变量。

~~~html
<input type="hidden" name="名字" valud="1000" />
~~~

### 列表

#### `<select>`和`<option>`

 标记是和  标记配合使用的，一个  标记就是下拉菜单中的一项，  标记和 标记的属性分别如下表所示。

**`select`标签属性**

> **size:** 指定下拉菜单中显的菜单项数目
>
> **multiple:**  若被加入，表标可同时选中下拉菜单中的多个菜单项，否则只能选择一个，没有属性值。

**`option`标签属性**

> **value**：指定的菜单项被选中后传送到服务器的实际值，可选，如果是省略，则将显示内容传到服务器
>
> **selected**：若被加入，表示默认选中，值是 **selected**

#### `<datalist>`标签

**`<datalist>`**虽然也可以生成列表，但是不能独立使用这个表单。  标记必须和一个可输入文本框类型 一起配合使用。

**基本语法**

~~~html
<input type="text" list="要绑定的datalist的id" name="名称" />
	<datalist id="列表" >
    	<option label="列表项的说明" val="列表项的值" />
	</datalist>
~~~

### `<input>`标签高级属性

#### `url`类型

定义url类型的输入表单，是在input标记中设置type属性值为url。当提交数据时，该表单会对输入的路径值自动进 行验证，输入的是不合法路径时会有提示语句。

**基本语法**

```html
<input type="url" name="名称" />
```

#### `email`类型

邮箱类型 

**基本语法**

```html
<input type="email" name="名称" />
```

#### 日期和时间

**基本语法**

```html
<input type="time" name="时间" />
<input type="date" name="日期" />
<input type="datetime" name="日期时间" />
<input type="datetime-local" name="日期时间型输入框" />
```

#### 数字类型

如果要在HTML5中输入整数，有两种数字类型可以实现number和range，这两种类型的属性都是一样的，唯一不 同之处在于页面中的展示形式。

**基本语法**

```html
<input type="range或number" name="=名称" min="最小值" max="最大值" step="步长" value="初始值" />
```

```html
<!DOCTYPE html>
<html>
	<head>
		<title>数字表单</title>
	</head>
	<body>
		<form>
<!--输入0—100之间的数字-->
			<input type="range" name="inputNum3" min="1" max="100" value="30"/>
<br/><br/>
<!--输入10-50之间的数字(步长为2)-->
			<input type="number" name="inputNum2" min="10" max="50" step="2" />
		</form>
	</body>
</html>
```

#### `color`类型

HTML5提供了type为color的input表单，打破了以前设计网页时，如果想要任意选择一种颜色，必须依赖编辑工具 的帮助。用户使用color新型表单控件可以通过鼠标在调色板上自由的选择颜色。

**基本语法**

```html
<input type="color" name="名称" />
```

#### `fieldset`控件组

 标记用于对同一个表单中的控件进行分组，也可以将一个网页上的不同表单进行分组，  标 记与  标记搭配使用，  标记可以为该控件组定义一个标题。

**基本语法**

```html
<form>
    <fieldset>
        <legend>按件组的标题</legend>
        ……
    </fieldset>
</form>
```

~~~html
<!DOCTYPE HTML>
<html>
	<head>
		<title>控件组</title>
	</head>
	<body>
		<form>
			<fieldset>
			<legend>用户登录</legend><br/>
				用户名：<input type="text" name="uname" />
				<br /><br />
				密&nbsp;码：<input type="password" name="upass" />
				<br /><br />
				<input type="submit" value="提交"/>
			</fieldset>
		</form>
	</body>
</html>
~~~

### 常用表单属性

#### `autofocus`属性

**autofocus** 属性可以让页面的某个表单元素在页面加载完成后自动地获得焦点。

**基本语法**

```html
<input autofocus="autofocus" />
```

#### `multiple`属性

`multiple`属性适用于file类型或者select的  标记。 multiple 属性设置了这种输入框可以同时选中多个 输入值。

**基本语法**

```html
<input type="file" multiple="multiple" />
```

#### `placeholder`属性

```html
<!DOCTYPE HTML>
<html>
	<head>
		<title>文本框提示语句</title>
	</head>
	<body>
		<form>
			邮箱地址：<input type="email" name="user_email" placeholder="请输入正确的		邮箱地址" />
			<input type="submit" value="提交"/>
		</form>
	</body>
</html>
```

#### `required`属性

`required` 属性是一个可用于各种表单的通用属性，该属性的作用是检测输入的内容是否为空，但不负责验证数据 是否合法。

**基本语法**

```html
<inpu required="required" />
```

```html
<!DOCTYPE HTML>
<html>
	<head>
		<title>文本框提示语句</title>
	</head>
	<body>
		<form>	
			邮箱地址：<input type="email" name="user_email" placeholder="请输入正确的邮箱地址" required="required" />
			<input type="submit" value="提交"/>
		</form>
	</body>
</html>
```

#### `pattern`属性

`pattern`属性的作用相当于给input输入域加上一个验证模式，这个验证模式（pattern）是一个正则表达式。在提 交时，会将输入框中的内容与表达式进行匹配，如果不符，则提示错误信息。

**基本语法**

~~~html
<input pattern="正则表达式" />
~~~

```html
<!DOCTYPE HTML>
<html>
	<head>
		<title>input元素中pattern属性的使用</title>
	</head>
	<body>
		<form>
		<fieldset>
			<legend>pattern属性：</legend>输入用户名
    			<input name="txtAge" type="text" pattern="^[a-zA-Z]\w{6,8}$" />
			<input name="frmSubmit" type="submit" value="提交" />
			<br/>
            <!--以字母开头,包含字符或数字和下划线,长度在6~8之间-->
		</fieldset>
		</form>
	</body>
</html
```

# 动画效果

## transform(变换)

### 属性-translate(平移)

```html
transanslate(水平移动距离，垂直移动距离);
<!--
取值:正负都可以
1.像素单位数值
2.百分比(参照物盒子自身的尺寸)

translate如果只给出一个值,表示x轴方向移动距离
单独设置某个方向的移动距离   translateX  和 translateY
```

### 属性-rotate(旋转)

```html
transform: rotate(角度);
<!--
角度单位是deg
取值正负均可
取值为正，顺时针旋转
取值为负，逆时针旋转
```

**盒子原点`transform-origin`**

```html
<!--
默认原点是盒子中心
-->
transform-orgin:原点水平位置 原点垂直位置;
<!--
改变原点
方位名词(left,top,right,bottom,center)
像素单位数值
百分比(参照盒子自身尺寸计算)
```

## animation动画效果

> 使用animation添加动画效果

动画效果：实现多个状态间的变化过程，动画过程可控(重复播放，最终画面，是否暂停)

```css
/* 步骤 */
/* 1. 定义动画 */
@keyframes 动画名称 {
    from {}
    to {}
}
@keyframes 动画名称 {
    0%||form {}
    10% {}
    20% {}
    50% {}
    100%||to {}
}
/* 使用动画 */
animation: 动画名称 动画花费时长;
```

```css
animation: 动画名 动画时长 速度曲线 延迟时间 重复次数 动画方向 执行完毕时的状态;
/*
动画名称和动时长必须赋值
取值不分先后顺序
如果右2个时间值
	第一个时间表示动画时长
	第二个时间表示动画延迟时间
```

### animation属性

| 值                        | 说明                                                         |
| ------------------------- | ------------------------------------------------------------ |
| animation-name            | 指定要绑定到选择器的关键帧的名称                             |
| animation-duration        | 动画指定需要多少称或毫秒完成                                 |
| animation-timing-function | 设置动画将如何完成一个周期                                   |
| animation-iteration-count | 定义动播放次数                                               |
| animation-fill-mode       | 规定当动画不播放时（当动画完成时，或当动画有一个延迟未开始播放时），要应用到元素的样式。 |

> **duration**：持续时间

#### animation-name 属性

| 值   | 说明                                                    |
| ---- | ------------------------------------------------------- |
| time | 指定动播完成花费的时间。默认值为0，意味着没有动画效果。 |

#### animation-duration 属性

| 值   | 说明                                                    |
| ---- | ------------------------------------------------------- |
| time | 指定动播放完成花费的时间。默认值为0，意味着没有动画效果 |

#### animation-timing-function 属性 

| 值                            | 说明                                                         |
| ----------------------------- | ------------------------------------------------------------ |
| linear                        | 动画从头到尾的速度是相同的。                                 |
| ease                          | 默认。动画以低速开始，然后加快，在结束前变慢。               |
| ease-in                       | 动画以低速开始。                                             |
| ease-out                      | 动画以低速结束。                                             |
| ease-in-out                   | 动画以低速开始和结束。                                       |
| steps(int,start\|end)         | 指定了时间函数中的间隔数里(步长)。有两个参数，第一个参数指定函数的间隔数，该参数是正整数(大于0)。第二个参数是可选的，表示动画是从时间段的开头连续还是末尾连续。含义分别如下：start：表示直接开始。end：默认值，表示直接开始 |
| cubic-bezier(*n*,*n*,*n*,*n*) | 在 cubic-bezier 函数中自己的值。可能的值是从 0 到 1 的数值。 |

> **int**：整数
>
> **start**：开始
>
> **end**：结束

#### animation-iteration-count 属性

| 值       | 描述                             |
| -------- | -------------------------------- |
| n        | 一个数字，定义应用播放多少次动画 |
| infinite | 指定动画应该播放无限次(永远)     |

#### animation-fill-mode 属性

```css
animation-fill-mode: none|forwards|backward|both|inital|inherit;
```

| 值        | 描述                                                         |
| --------- | ------------------------------------------------------------ |
| none      | 默认值，动在动画执行之前和之后不会应用任何样式到目标元素     |
| forwards  | 在动画结束后(由animation-iteration-count决定)，动画将应用该属性性值。 |
| backwards | 动画将应用在 animation-delay 定义期间启动动画的第一次迭代的关键帧中定义的属性值。这些都是 from 关键帧中的值（当 animation-direction 为 "normal" 或 "alternate" 时）或 to 关键帧中的值（当 animation-direction 为 "reverse" 或 "alternate-reverse" 时）。 |
| both      | 动画遵循 forwards 和 backwards 的规则。也就是说，动画会在两个方向上扩展动画属性。 |






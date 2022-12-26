# 2D转换

## 简介

**转换`transform`**是CSS3中具有颠覆性的特征之一，可以实现元素的位移，旋转，缩放等效果

转换(transform)你可以简单理解为变形

* 移动：**`translate`**
* 旋转：**`rotate`**
* 缩放：**`scale`**

**二维坐标系**

> 2D转换是改变标签在二维平面上的位置和形状的一种技术

## 2D转换移动 translate

### 用法

2D移动是2D移换里面的一种功能，可以改变元素在页面的位置，类似**定位**。

**语法**

```css
transform: translate(x,y);
/* 或者分开写 */
transform: translateX(n);
transform: translateY(n);
/* 注意分开写的话它们俩个算相同样式会被覆盖掉 */
```

**重点**

* 定义2D转换中的移动，沿着X和Y轴移动的元素
* **`translate`最大的优点：不会影响到其他元素的位置**
* `translate`中的百分比单位是相对于自身元素的`translate: (50%,50%)`;
* 对行内标签没有效果

## 2D转换旋转 rotate

### 用法

2D旋转指的是让元素在2维平面内顺时针旋转或者逆时针旋转。

**语法**

```css
transform: rotate(度数);
transform: rotate(60deg);
```

**重点**

* **`rotate`**里面跟度数，单位是deg比如 `rotate(45deg)`
* 角度为正时，顺时针，负时，为逆时针
* 默认旋转的中心点是元素的中心点

### 案例：三角形

```css
triangle {
    width: 15px;
    height: 15px;
    border-right: 1px solid #000;
    border-bottom: 1px solid #000;
    transform: rotate(45deg);
}
```

## 2D转换中心点 transform-origin

### 用法

我们可以设置元素转换的中心点

**语法**

```css
transform-origin: x y;
```

**重点**

* 注意后面的参数 x 和 y 用空格隔开
* x y默认转换的中心是元素的中心点(50% 50%)
* 还可以给x y设置像素或者 方位名词 (top bottom left right center)

## 2D转换缩放 scale

### 用法

缩放，可以放大和缩小。只要元素添加上这个属性就能控制它放大还是缩小。

**语法**

```css
transform: scale(x,y);
/* 注意缩放是用逗号隔开的 */
```

**注意**

* **注意其中的x和y用逗号分隔**
* **`transform: scale(1,1)`**：宽和高都放大一倍，相对于没有放大
* **`transform: scale(2,2)`**：宽和高都放大了2倍
* **`transform: scale(2)`**：只写一个参数，第二个参数则和第一个参数一样，相当 `scale(2,2)`
* **`transform: scale(0.5,0.5)`**：缩小
* `sacle`缩放最大的优势：可以设置转换中心点缩放，默认以中心缩放的，**而且不影响其他盒子**
  * 还可以设置缩放中心点

## 2D转换综合写法

**注意**

1. 同时使用多个转换，其格式为：`transform: translate() rotate() scale()`...等
2. 其顺序会影响转换的效果。**先旋转会改变坐标轴方向**
3. **当我们同时有位移和其他属性的时候，记得要将位移放到最前面**

# 动画

## 简介

**动画(animation)**是CSS3中具有颠覆性的特征之一，可通过设置多个节点来精确控制一个或一组动画，常用来实现复杂的动画效果

相比较过渡，动画可以实现更多变化，更多控制，连续自动播放等效果。

## 动画的基本使用

制作动画分为两步：

1. 先定义动画
2. 再使用(调用)动画

**1. 用`@keyframes`定义动画(类似定义类选择器)**

```css
@keyframes 动画名称 {
    0% {
        width: 100px;
    }
    100% {
        width: 200px;
	}
}
```

**2. 元素使用动画**

```css
div {
    width: 200px;
    height: 200px;
    background-color: red;
    /* 调用动画 */
    animation-name: 动画名称;
    /* 持续时间 */
	animation-duration: 持续时间;
}
```

## 动画序列

* 0%是动画的**开始**，100%是动画的**完成**。这样的规则就是动画序列。
* 在`@keyframes`中规定某项CSS样式，就能创建由当前样式逐渐改为新样式的动画效果
* 动画是使元素从一种样式逐渐变化为另种一样式的效果。你可以改变任意多的**次数**。
* 请用百分比规定变化发生的时间，或用关键词**from**和**to**，等同于**0%**和**100%**。

> 里面的百分比是 总的时间划分

## 动画常用属性

| 属性                      | 说明                                                         |
| ------------------------- | ------------------------------------------------------------ |
| @keyframes                | 规定动画                                                     |
| animation                 | 所有动画属性的简写属性，除了animation-play-state属性         |
| animation-name            | 规定@keyframes动画的名称。**必须的**                         |
| animation-duration        | 规定动画完成一个周期所花费的秒或毫秒，默认是0。(必须的)      |
| animation-timing-function | 规定动画的速度曲线，默认是 **ease**                          |
| animation-delay           | 规定动画何时开始，默认是0                                    |
| animation-iteration-count | 规定动画被播放的次数，默认是1，还有infinite                  |
| animation-direction       | 规定动是否在下一周期逆向播放，默认是**normal**, **alternate**逆播放 |
| animation-play-state      | 规定动画是否正在运行或暂停。默认是**running**,还有**paused** |
| animation-fill-mode       | 规定动结束后状态，保持**forwards** 回到起始**backwards**     |

> **animation-fill-mode**
>
> 这个属性跟无限播放和往回播放冲突，用时记的要把那个俩个注释掉

## 动画简写

### 用法

```css
animation: 动画名称 持续时间 运动曲线 何时开始 播放次数 是否反方向 动画起始或者结束的状态;
animation: name 5s linear 2s infinite alternate;
/* 注意 */
/*
这里面有俩个时间，持续时间在最前面，何时开始在持续时间后面写
*/
```

* 简写属性里面不包含**`animation-play-state`**
* 暂停动画：**`animation-play-state: puased;`**经常和鼠标经过等其他配合使用
* 想要动画走回来，而不是直接跳回来：**`animation-direction: alternate;`**
* 盒子动画结束后，停在结束位置：**`animation-fill-mode: forwards;`**

###  opacity 透明度

**语法**

```css
opacity: 1;
/* 没有单位 如果想变成透明的小于1 */
/*
opacity: 不透明度
*/
```

## 速度曲线 animation-timing-function

**`animation-timing-function`**：规定动画的速度曲线，默认是**ease**

| 值          | 描述                                         |
| ----------- | -------------------------------------------- |
| linear      | 动画从头到尾的速度是相同的。匀速             |
| ease        | 默认。动画以低速开始，然后加快，在结束前变慢 |
| ease-in     | 动画以低速开始。                             |
| ease-out    | 动画以低速结束。                             |
| ease-in-out | 动画以低速开始和结束                         |
| steps()     | 指定了时间函数中的间隔数量(步长)             |

### 打字机效果

```css
div {
    overflow: hidden;
    font-size: 20px;
    width: 0;
    height: 30px;
    /* 让文字强制一行内显示 */
	white-space: nowrap;
    /* steps 就是分几步来完成我们动画 有了steps就不要在写ease或者linear */
    animartion: w 4s steps(6) forwards;
}
@keyframes w {
    to {
		width: 600px;
    }
}
```

## 添加多个动画

### 用法

```css
/* 我们元素可以添加多个动画，用逗号公隔 */
animation: bear 1s steps(8) infinite, move 1s forwards;
```

# 3D转换

## 简介

我们生活中的环境是3D的，照片就是3D物体在2D平面呈现的例子。

**有什么特点**

* 近大远小
* 物体后面遮挡不可见

## 三维坐标系

三维坐标系其实就是指立体空间，立体空间是由3个轴共同组成的。

* x轴：水平向右     **注意： X右边是正值，左边是负值**
* y轴：垂直向下     **注意：Y下面是正值，上面是负值**
* z轴：垂直屏幕     **注意：往外面是正值，往里面是负值**

![三维坐标系](F:\图片\截图\三维坐标系.png)

## 透视 perspective

在2D平面产生近大远小视觉立体，但是只是效果二维的

* 如果想要在网页产生3D效果需要透视(理解成3D物体投影在2D平面内)。
* 模拟人类的视类位置，可以认为安排一只眼去看
* 透视我们也称为视距：视距就是人的眼睛到屏幕的距离
* 距离视觉点越近的在电脑平面成像越大，越远成像越小
* 透视的单位是像素

![透视](F:\图片\截图\透视.png)

**注意**

> 透视写在被观察元素的父盒子上面
>
> d：就是视距，视距就是一个距离人的眼睛到屏幕的距离
>
> z：就是z轴，物体距离屏幕的距离，z轴越大(正值)我们看到的物体就越大



## 3D转换 位移和旋转

### 简介

**主要知识点**

* 3D移动：**`translate3d(x,y,z)`**
* 3D旋转：**`rotate3d(x,y,z)`**
* 透视：**`perspective: 500px;`**
* 3D呈现：**`transform-style`**

### 3D移动 translate3d

3D移动在2D移动的基础上多加了一个可以移动的方向，就是z轴方向。

* **`transform: translateX(100px);`**：仅仅是在x轴上移动
* **`transform: translateY(100px);`**：仅仅是在Y轴上移动
* **`transform： translateZ(100px);`**：仅仅是在Z轴上移动(注意：translateZ一般用px单位)
* **`transform: translate3d(x,y,z);`**：其中x，y，z分别指要移动的轴的方向的距离

**注意**

> 它们可以合着写但用空格隔开
>
> ```css
> transform: translateX(100px) translateY(100px) translateZ(100px);
> transform: translate3d(100px,100px,100px);
> /* 它们是相同样式会被覆盖掉 */
> ```
>

#### translateZ

**`transform: translateZ(100px);`**：仅仅是在Z轴上移动有了透视，就能看到translateZ引起的变化了

### 3D 旋转 rotate3d

#### 简介

3D旋转指可以让元素在三维平面内沿着x轴，y轴，z轴或者自定义进行旋转。

**语法**

* **`tranform: rotateX(45deg);`**：沿着X轴正方向旋转45deg，deg单位代表度
* **`tranform: rotateY(45deg);`**：沿着Y轴正方向旋转45deg
* **`tranform: rotateZ(45deg);`**：沿着Z轴正方向旋转45deg
* **`tranform: rotate3d(x,y,z,deg);`**：沿着自定义轴旋转deg为角度(了解即可)

#### rotateX

沿着X轴旋转，类似于我们生中活的单扛，正值旋转底下向前翻转，顶部往后翻转

#### rotateY

沿着Y轴旋转，类似钢管舞，正值是左边往前翻转，右面往后翻转

#### rotateZ

Z轴眼睛到屏幕之间平行的线旋转，和2D的旋转一样。和生活中的转盘类似

#### rotate3d

**`tranform: rotate3d(x,y,z,deg);`**：沿着自定义轴旋转deg为角度

xyz是表示旋转轴的矢量，是标示你是否希望沿着该旋转，最后一个标示旋转的角度。

* **`tranform: rotate3d(1,0,0,45deg);`**就是沿着x轴旋转45deg
* **`tranform: rotate3d(1,1,0,45deg);`**就是沿着对角线旋转45deg

## 3D呈现 transfrom-style

* 按制子元素是否开启三维立体环境
* **`transform-style: flat`**子元素不开启3d立体空间 默认的
* **`tranform-style: preserve-3d;`**子元素开启立体空间，保留子元素的立体空间
* **代码写给父级，但是影响的是子盒子**
* 这个属性很重要，后面必用

# 浏览器私有前缀

浏览器私有前缀是为了兼容老版的写法，比较新版本的浏览器无须添加。

**私有前缀**

* -moz-：代表firefox 浏览器私有属性
* -ms-：代表ie浏览器私有属性
* -webkit-：代表safari、chrome私有属性
* -o-：代表Opera私有属性

**提倡的写法**

```CSS
-moz-border-radius: 10px;
-webkit-border-radius: 10px;
-o-border-radius: 10px;
borde
```





















































 














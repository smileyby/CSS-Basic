CSS简介和语法
============

## CSS简介
* CSS指的是层叠样式表（Cascading Style Sheets），为了解决内容与表现分离的问题，可以大大提高工作效率，多个样式层叠为一也可以节省代码的重复
* 在很久很久以前，只是用html来进行布局，有关样式的部分使用html属性完成，这样代码就显得臃肿，修改起来也特别的麻烦。后来W3C就创造了样式（style），这样html就只负责结构，描述样式就交给了css。这样大大减少了开发者的工作量，提高了工作效率

## CSS基本语法
* CSS规则由两个主要的部分构成：选择器，以及一条或多条声明（CSS属性）
* 选择器通常是您需要改变样式的HTML元素
* 每跳声明有一个属性和一个值组成
* 属性是你希望设置的样式属性。每个属性有一个值。属性和值被冒号隔开

## CSS引入方式

* 行内式：通过style这个标签属性，将css键值对写入标签内

```html
<p style="width: 100px;height: 100px;backgrounf-color: red;"></p>
<!-- 这段代码是描述一个宽高为100像素，背景色为红色的一个p标签 -->
```

* 内嵌式（嵌入式）：使用style标签将css属性名和属性值引入到html页面中，通常style标签放置在head标签中。为什么css样式要放置在head标签中呢，因为代码从上到下执行，如果现价在结构，那么用户看到的就讲师干巴巴的内容，而没有通过美化，而现加载样式后加载结构，将相当于孩子出生就穿着衣服（style可以放在body和head中，建议放在head标签内title下）

```html
<head>
	<style>
		p {
			width: 100px;
			height: 100px;
			background: red;
		}
	</style>
</head>
<!-- 这段代码也是描述狂爱为100像素，背景色为红色的一个p标签，只不过是通过内嵌的方法引入 -->
```

* 外联式（外链式）：通过link标签将独立的css文件引入到html文件中

```html

<link rel="stylesheet" type="text/css" href="../css/prism.css">
<!-- rel="stylesheet" 描述了当前页面与href所指定文档的关系，即说明的是href链接的文档是一个样式表; -->
<!-- type="text/css" 是指定MIME类型，也就是css文档 -->
<!-- href="../css/prism.css"规定被链接文档的位置 -->
```

* 导入式：通过@import'URL'引入独立css文件
**如果style里面既有内嵌的样式 又有导入式的样式导入式要放在内嵌式的上面；放在下面会报错导致导入式的样式直接失效。**

```html
<style type="text/css">
	@import url(style.css)
</style>
<!-- url(style.css) url（规定被链接文档的位置） -->
```

## CSS引入方式 - 外联式和导入式的区别

* link和@import虽然都是引入外部的css文件，但是他们是有很大区别的
* link是html标签，@import完全是css提供的方式，要写在css文件或者style标签中。
* 他们的加载顺序也是有区别的，当一个页面被加载的时候，link引用的css文件会被同时加载，而@import引入的css文件会等页面全部下载完成后再加载
* 当使用javascript控制DOM去改变css样式的时候，只能使用link标签，因为import是不能被DOM控制的。**为什么js不能操作import引入的样式？**

## CSS命名规范

1. 必须使用英文开头，并且开头英文一律小写
2. 所有的命名最好都小写
3. 尽量不要用缩写，除非一目了然
4. 如果遇到相差不大class或者id，主功能识别字母在前，位置识别字母在后，位置识别字母第一个可大写（如：navTop，menuLeft）
5. 遵循驼峰命名法：第一个单词的首字母小写，其余每一个有意义的单词首字母大写（如：studentIndo，getElementById）

<table>
	<tr>
		<td>头</td>
		<td>header</td>
	</tr>
	<tr>
		<td>内容</td>
		<td>content&gt;/container</td>
	</tr>
	<tr>
		<td>尾</td>
		<td>footer</td>
	</tr>
	<tr>
		<td>导航</td>
		<td>nav</td>
	</tr>
	<tr>
		<td>侧边栏</td>
		<td>sidebar</td>
	</tr>
	<tr>
		<td>栏目</td>
		<td>column</td>
	</tr>
	<tr>
		<td>页面外围控制整体布局宽度</td>
		<td>wrapper</td>
	</tr>
	<tr>
		<td>左右中</td>
		<td>left right center</td>
	</tr>
	<tr>
		<td>登录条</td>
		<td>loginbar</td>
	</tr>
	<tr>
		<td>标志</td>
		<td>logo</td>
	</tr>
	<tr>
		<td>广告</td>
		<td>banner</td>
	</tr>
	<tr>
		<td>页面主体</td>
		<td>main</td>
	</tr>
</table>

## CSS选择器

* CSS规则由两个主要的部分构成：选择器，以及一条或多条声明（css属性）
* 选择器通常是您需要改变样式的HTML元素
* 每条声明由一个属性和一个值组成
* 属性是你希望设置的样式属性。每个属性有一个值。属性和值被冒号分开

### CSS选择器 - 基本选择器
* 标签选择器：直接使用元素标签进行选择<p></p> p{color: red;} => 次选择器的权重为1
* 类选择器：通过元素的类名来选择元素。一个元素可以有多个类名，都代表这个元素类名是元素class属性中的属性值，例如<p class="sum"></p> .sum{} => 此选择器的权重为10
* id选择器：通过元素的id名，来选择元素，类名是元素id属性中的属性值，例如<p id="sum"></p> #sum{} => 次选择器的权重为100
* 通配符选择器：通过*选择全部元素，包括根元素 *{} => 权重小于1，可被覆盖

### CSS选择器 - 并集选择器
* 你可以对选择器进行分组，这样，被分组的选择器就可以分享相同的声明。用逗号将需要分组的选择器分开。在下面的例子中，我们队所有的标题元素进行了分组。所有的标题都是绿色。

```css
h1,h2,h3,h4,h5,h6, {
	color: green;
}
```

### CSS选择器 - 交集选择器
* 两种属性同一个元素的时候，我们可以使用交集选择器来进行元素的准确选择

```html
<p class="name1 name2" id="id1"></p>
```

```css
p.name1 {}
p#id1 {}
.name1.name2 {}
```

### CSS选择器 - 派生（后代）选择器
* 通过一句元素在其位置的上下文关系来定义样式，你可以使标记更加简洁，用空格隔开列表中的strong元素变为斜体，而不是通常的粗字体，可以这样定义一个派生选择器
* 后代选择器尽量不要超过3个，没必要把每一个层级都写出来，只需要写出关键节点即可

```html
<ol>
	<li><strong>我是斜体字。这是因为strong元素位于li元素内</strong></li>
</ol> 
```

```css
li strong {
	font-style: italic;
	font-weight: normal;
}
```

### CSS选择器 - 子选择器
* 与后台选择器想必，子元素选择器只能选择作为某元素子元素的元素，符号为大括号；
* 子代选择器只作用于儿子这一代，孙子以及孙子后面的子代不受影响

```html
<sytyle>
	h1 > strong {color:red;}
</style>
<h1>This is <strong>very</strong> <strong>very</strong> important.</h1>
```

```html
<!-- div的子元素只有p标签 span不能算div的子元素 只能算是孙子元素 -->
<div>
	<p>内容1<span>内容2</span></p>
</div>
```

### CSS选择器 - 兄弟（~）和相邻兄弟选择器(+)
* 相邻兄弟选择器（+）：可以选择紧接在一个元素后的元素，且二者都有相同的父元素。
* 兄弟选择器（~）：可以选择紧接在一个元素后的所有兄弟元素

```html
<style>
	strong+span {
		background-color: #ff6700;
	}
	strong~span {
		background-color: red;
	}
</style>
<div>
	<span>1111</span>
	<strong>2222</strong>
	<span>3333</span>
	<span>4444</span>	
</div>
```

### CSS选择器 - 属性选择器
* 对带有指定属性的HTML元素这只样式 权重为10，可以为拥有指定属性的HTML设置样式，而不仅限于class和id属性（属性可以是自带的，也可以是自定义的标签属性）
> 属性选择器
> `[title]{color:red;}`
> 属性和值选择器
> `[title=zfpx]{border:1px solid blue;}`
> 设置表单的样式
> `input[type="text"]{width:150px;display:block;background-color:yellow;}`

### CSS选择器 - 伪类选择器
* a:link {color: #ff0000}  未访问的链接
* a:visited {color: #00ff00} 已访问链接
* a:hover {color: #ff00ff} 鼠标移动到连接上
* a:active {color: #0000ff} 选定的链接（鼠标按下没有抬起时的效果）

**注意：href="#" a:visited{color:red;}不起作用；href="https://www.baidu.com" a:visited{color:red;}起作用**

<table>
	<tr>
		<td>属性</td>
		<td>描述</td>
	</tr>
	<tr>
		<td>:active</td>
		<td>向北激活的元素添加样式</td>
	</tr>
	<tr>
		<td>:focus</td>
		<td>项拥有键盘输入焦点的元素添加样式</td>
	</tr>
	<tr>
		<td>:hover</td>
		<td>当鼠标悬浮在元素上方时，湘元素添加样式</td>
	</tr>
	<tr>
		<td>:link</td>
		<td>向未被访问的链接添加样式</td>
	</tr>
	<tr>
		<td>:visited</td>
		<td>项已被访问的链接添加样式</td>
	</tr>
	<tr>
		<td>:first-child</td>
		<td>项元素的第一个子元素添加样式</td>
	</tr>
	<tr>
		<td>:lang</td>
		<td>项带有指定lang属性的元素添加样式</td>
	</tr>
</table>

### CSS3新增伪类选择器
> :not(X) css否定伪类，是以一个简单的以选择器X为参数的功能性标记函数。它匹配不符合参数选择器X描述的元素。X不能包含另外一个否定选择器。

```css
/* 类名不是'.fancy'的<p>元素 */
p:not(.fancy) {
	color: green;
}

/* 非<p>元素 */
body :not(p) {
	text-decoration: underline;
}

/* 非<div>或<span>的元素 */
body :not(div):not(span) {
	font-weight: bold;
}

/* 类名不是 '.crazy' or '.fancy'的元素 */
/*注意，词语发尚未被较好地支持*/
body :not(.crazy, .fancy) {
	font-family: sans-serif;
}
```

> :last-child css伪类代表父元素的最后一个子元素

```html
<ul>
	<li>次元素背景色不是lime</li>
	<li>我的也不是lime</li>
	<li>我的才是lime</li>
</ul>
```
```css
/* 注意是作用在子元素上的最后一个子元素 */
li:last-child {
	background-color: lime;
}
```
> :nth-child(an+b) 这个css伪类匹配文档树种在其之前具有an+b-1个兄弟节点的元素，其中n为正值或零值。简单点说就睡，这个选择器匹配那些在同系列兄弟节点中的位置与模式an+b匹配的元素。**an+b>=1**
>>
* 1n+0或简单的n匹配每个元素
* 2n+0或简单的2n匹配位置为2、4/6/8...的元素，你可以使用关键字**even**来替代此表达式
* 2n+1匹配位置为1、3/5/7...的元素。你可以使用关键字**odd**来替换此表达式 
 
> :only-child 代表了属于某个父元素的唯一一个子元素，等效的选择器还可以写成`:first-child:last-child` 或 `:nth-child(1):nth-last-child(1)`，当然前者的权重会低一点。
> [点击查看-详细展示效果](https://codepen.io/smileyby/pen/jKJKYp)
> :nth-last-child 这个CSS伪类匹配文档树中在其后具有`an+b-1`个兄弟节点的元素，其中n为正值或零值。它基本上和`:nth-child` 一样，只是它从**结尾**处反序技术，而不是从开头处。
> :first-of-type 这个CSS伪类表示一组兄弟元素中其类型的第一个元素
>> [点击查看-选择第一个段落](https://codepen.io/smileyby/pen/rKRKJb)
>> [点击查看-这个例子展示了当没有写简单选择器时，通配选择器是如何被假定的。](https://codepen.io/smileyby/pen/xzBzjb)

> :last-of-type 这个CSS伪类表示在（它父元素的）子元素列表中，最后一个给定类型的元素。当代码类似Parent tagName：last-of-type的作用区域包含父元素的所有子元素中的最后一个选定元素，也包括子元素的最后一个子元素并以此类推。
>> [点击查看-具体示例](https://codepen.io/smileyby/pen/vrPrpy) 

> :only-of-type 这个CSS伪类匹配文档书中在其之前具有`an+b-1`个相同兄弟节点的元素，其中n为正值或零值。
>> [点击查看-基础示例](https://codepen.io/smileyby/pen/eKXKja)
 
> :nth-of-type(n) 这个CSS伪类匹配文档树中在其之前具有`an+b-1`个相同兄弟节点的元素，其中n为正值或零值。
>> [点击查看-基础示例](https://codepen.io/smileyby/pen/BVbVGY) 

> :nth-last-of-type(an+b) 它基本上和 :nth-of-type 一样，只是它从结尾处反序计数，而不是从开头处。
>> [点击查看-基础示例](https://codepen.io/smileyby/pen/qKvKzN) 

> :empty 这个CSS伪类代表没有子元素的元素。子元素只可以是元素节点会文本（包括空格），无论一个元素是否为（empty or nor），注释或处理指定都不会产生影响。
>> [点击查看-基础示例](https://codepen.io/smileyby/pen/YvgjKQ) 

> :checked 这个CSS伪类选择器表示任何处于选中状态的radio(<input type="radio">)，checkbox（<input type="checkbox">）或（“select”）元素中的option HTML元素。用户通过点击元素或选择其他的值，可以改变该元素的:check状态，并:check属性赋给一个新的对象。（例如其他的option值）
>> [点击查看-基础示例](https://codepen.io/smileyby/pen/GGeBqx) 

### CSS选择器 - 伪元素选择器
* :first-line 
> `::first-line`在某块级元素的第一行应用样式。第一行的长度取决于很多因素，包括元素宽度，文档宽度和文本字体大小
> 和其他所有的伪元素一样，::first-line不能匹配任何真实存在的html元素
> ::first-line伪元素只能在块容器中，所以`::firsty-line`伪元素只能在一个display值为`block`/`inline-block`/`table-cell`/`table-caption`中有用。其他的类型中，`::first-line`是不起作用的。
> css3写法：`::first-line`css2写法：`:first-line`

[点击查看-应用实例](https://codepen.io/smileyby/pen/ERzYOz)
* :first-letter
> 选中块级元素第一行的第一个字母
> **出于兼容性考虑，建议使用`:first-letter`**
[点击查看-效果示例](https://codepen.io/smileyby/pen/qKGBdO)
* :before
> `::before`创建一个伪元素，其将成为匹配选择中的元素的第一个子元素。常通过`content`属性来为一个元素添加修饰性的内容。此元素默认为行内元素。

[点击查看-示例效果1](https://codepen.io/smileyby/pen/QxRWdZ)
[点击查看-示例效果2](https://codepen.io/smileyby/pen/MXdWJd)
* :after
> `::before`创建一个伪元素，其将成为匹配选择中的元素的最后一个子元素。常通过`content`属性来为一个元素添加修饰性的内容。此元素默认为行内元素。

[点击查看-示例效果1](https://codepen.io/smileyby/pen/JZqjJX)
[点击查看-示例效果2](https://codepen.io/smileyby/pen/LroYLR)

### CSS权重和基本规则
* [CSS权重和基本规则](http://www.w3cplus.com/css/css-specificity-things-you-should-know.html)

### CSS - 可以继承和不可以继承的样式属性
> 一、无继承性的属性
1. display属性
2. 文本属性
3. 盒子模型类属性
4. 背景类
5. 浮动类
6. 定位类

> 二、可以继承的属性
1. 字体系列样式属性
2. 文本系列样式属性 text-align line-height text-indent

**text-indent:-9999px;首段缩进足够大，文字就会消失**

### 盒子模型
![盒子模型](https://mdn.mozillademos.org/files/72/boxmodel%20(1).png)
[点击查看-MDN盒子模型详解](https://developer.mozilla.org/zh-CN/docs/Web/CSS/CSS_Box_Model/Introduction_to_the_CSS_box_model)

> 关于盒子模型的宽度和高度

>> 摩拜 自然堂官网  百分比自适应 响应式
>>
>> CSS盒子模型内边距padding及简写
>>
* padding:10px; 上右下左
* padding: 10px 20px; 上下 左右
* padding: 10px 20px 30px; 上 左右 下
* padding: 10px 20px 30px 40px; 上右下左
* 内边距会影响盒子在浏览器中的实际大小

> 关于盒子模型border使用技巧
* border: [border-width ||border-style ||border-color |inherit]
* border-style 可能取值如下：

<table class="standard-table">
  <tbody>
   <tr>
    <td style="vertical-align: middle;"><code>none</code></td>
    <td style="vertical-align: middle;">
     <div style="border-width: 3px; margin: 0.5em; width: 3em; height: 3em; background-color: palegreen;">&nbsp;</div>
    </td>
    <td style="vertical-align: middle;">和关键字&nbsp;<code>hidden</code>&nbsp;类似，不显示边框。在这种情况下，如果没有设定背景图片，<a href="/zh-CN/docs/Web/CSS/border-width" title="The border-width property sets the width of the border of a box. Using the shorthand property border is often more convenient."><code>border-width</code></a> 计算后的值将是&nbsp;<code>0</code>，即使先前已经指定过它的值。在单元格边框重叠情况下，<code>none</code>&nbsp;值优先级最低，意味着如果存在其他的重叠边框，则会显示为那个边框。</td>
   </tr>
   <tr>
    <td style="vertical-align: middle;"><code>hidden</code></td>
    <td style="vertical-align: middle;">
     <div style="border-width: 3px; border-style: hidden; margin: 0.5em; width: 3em; height: 3em; background-color: palegreen;">&nbsp;</div>
    </td>
    <td style="vertical-align: middle;">和关键字&nbsp;<code>none</code>&nbsp;类似，不显示边框。<span style="font-size: 13.63636302948px; line-height: 19.0909080505371px;">在这种情况下，如果没有设定背景图片，<a href="/zh-CN/docs/Web/CSS/border-width" title="The border-width property sets the width of the border of a box. Using the shorthand property border is often more convenient."><code>border-width</code></a> 计算后的值将是&nbsp;</span><code style="font-style: normal; font-size: 13.63636302948px; line-height: 19.0909080505371px;">0</code><span style="font-size: 13.63636302948px; line-height: 19.0909080505371px;">，即使先前已经指定过它的值。在单元格边框重叠情况下，</span><code>hidden</code>&nbsp;值优先级最高，意味着如果存在其他的重叠边框，边框不会显示。</td>
   </tr>
   <tr>
    <td style="vertical-align: middle;"><code>dotted</code></td>
    <td style="vertical-align: middle;">
     <div style="border-width: 3px; border-style: dotted; margin: 0.5em; width: 3em; height: 3em; background-color: palegreen;">&nbsp;</div>
    </td>
    <td style="vertical-align: middle;">显示为一系列圆点。标准中没有定义两点之间的间隔大小，<span style="font-size: 13.63636302948px; line-height: 19.0909080505371px;">视不同实现而定</span>。圆点半径是 <a href="/zh-CN/docs/Web/CSS/border-width" title="The border-width property sets the width of the border of a box. Using the shorthand property border is often more convenient."><code>border-width</code></a> 计算值的一半。</td>
   </tr>
   <tr>
    <td style="vertical-align: middle;"><code>dashed</code></td>
    <td style="vertical-align: middle;">
     <div style="border-width: 3px; border-style: dashed; margin: 0.5em; width: 3em; height: 3em; background-color: palegreen;">&nbsp;</div>
    </td>
    <td style="vertical-align: middle;">显示为一系列短的方形虚线。标准中没有定义线段的长度和大小，视不同实现而定。</td>
   </tr>
   <tr>
    <td style="vertical-align: middle;"><code>solid</code></td>
    <td style="vertical-align: middle;">
     <div style="border-width: 3px; border-style: solid; margin: 0.5em; width: 3em; height: 3em; background-color: palegreen;">&nbsp;</div>
    </td>
    <td style="vertical-align: middle;">显示为一条实线。</td>
   </tr>
   <tr>
    <td style="vertical-align: middle;"><code>double</code></td>
    <td style="vertical-align: middle;">
     <div style="border-width: 3px; border-style: double; margin: 0.5em; width: 3em; height: 3em; background-color: palegreen;">&nbsp;</div>
    </td>
    <td style="vertical-align: middle;">显示为一条双实线，宽度是 <a href="/zh-CN/docs/Web/CSS/border-width" title="The border-width property sets the width of the border of a box. Using the shorthand property border is often more convenient."><code>border-width</code></a> 。</td>
   </tr>
   <tr>
    <td style="vertical-align: middle;"><code>groove</code></td>
    <td style="vertical-align: middle;">
     <div style="border-width: 3px; border-style: groove; margin: 0.5em; width: 3em; height: 3em; background-color: palegreen;">&nbsp;</div>
    </td>
    <td style="vertical-align: middle;">显示为有雕刻效果的边框，样式与&nbsp;<code>ridge</code>&nbsp;相反。</td>
   </tr>
   <tr>
    <td style="vertical-align: middle;"><code>ridge</code></td>
    <td style="vertical-align: middle;">
     <div style="border-width: 3px; border-style: ridge; margin: 0.5em; width: 3em; height: 3em; background-color: palegreen;">&nbsp;</div>
    </td>
    <td style="vertical-align: middle;">显示为有浮雕效果的边框，样式与&nbsp;<code>groove</code>&nbsp;相反。</td>
   </tr>
   <tr>
    <td style="vertical-align: middle;"><code>inset</code></td>
    <td style="vertical-align: middle;">
     <div style="border-width: 3px; border-style: inset; margin: 0.5em; width: 3em; height: 3em; background-color: palegreen;">&nbsp;</div>
    </td>
    <td style="vertical-align: middle;">显示为有陷入效果的边框，样式与&nbsp;<code>outset</code>&nbsp;相反。当它指定到 <a href="/zh-CN/docs/Web/CSS/border-collapse" title="border-collapse CSS 属性是用来决定表格的边框是分开的还是合并的。在分隔模式下，相邻的单元格都拥有独立的边框。在合并模式下，相邻单元格共享边框。"><code>border-collapse</code></a> 为 <code>collapsed</code>&nbsp;的单元格时，会显示为&nbsp;<code>groove</code>&nbsp;的样式。</td>
   </tr>
   <tr>
    <td style="vertical-align: middle;"><code>outset</code></td>
    <td style="vertical-align: middle;">
     <div style="border-width: 3px; border-style: outset; margin: 0.5em; width: 3em; height: 3em; background-color: palegreen;">&nbsp;</div>
    </td>
    <td style="vertical-align: middle;">
     <p>显示为有突出效果的边框，样式与&nbsp;<code>inset</code>&nbsp;相反。当它指定到 <a href="/zh-CN/docs/Web/CSS/border-collapse" title="border-collapse CSS 属性是用来决定表格的边框是分开的还是合并的。在分隔模式下，相邻的单元格都拥有独立的边框。在合并模式下，相邻单元格共享边框。"><code>border-collapse</code></a> 为&nbsp;<code>collapsed</code>&nbsp;的单元格时，会显示为&nbsp;<code>ridge</code>&nbsp;的样式。</p>
    </td>
   </tr>
  </tbody>
 </table>

**如果border属性只有边框宽度 没有border-style和border-color，会导致border属性失效**

* 使用border属性做箭头和小三角形
> 三角箭头的实现原理：先实现正方形的任意相邻的两条边线，然后旋转一定角度得到我们任意方向的箭头
> 小三角的大小由正方形的宽高决定
> 小三角的粗细由border边框线的宽度决定
> 三角形的实现原理：利用border的3个属性border-width/border-style/border-color去实现，宽度和高度为0，实现由四个小三角组成的正方形；

```css
.arrow {
	width: 200px;
	height: 200px;
	border-top: 10px solid #000;
	border-left: 10px solid #000;
	transform: rotate(45deg);
}
.triangle {
	width: 0;
	height: 0;
	border-width: 100px;
	border-style: solid;
	border-color: red transparent transparent transparent;
}
```
[点击查看-具体效果](https://codepen.io/smileyby/pen/BVbGGE)

* margin值和垂直边距重叠问题
> margin: 10px; 上有下左
> margin: 10px 20px; 上下 左右
> margin: 10px 20px 30px; 上 左右 下
> margin: 10px 20px 30px 40px; 上 右 下 左

**（垂直方向）一个盒子有上边距 另一个有下边距 会出现margin边距的重叠问题，取边距大的为间隔，并不是两个margin之和**

* margin兼容之margin-top的传递问题
> 大盒子里面嵌套一个小盒子，给小盒子加margin-top值，不但没有实现和大盒子之间的距离，而是整体下移
> 
> 解决兼容问题：
1. overflow:hidden; 解决margin-top的传递问题（此处并不是溢出隐藏）
2. padding-top:1px; 这种方法会影响最后实际的高度 需要在高度height基础上减掉才不会影响实际的高度
3. border-top:1px; 这种方法会影响最后实际的高度，需要在高度height基础上减掉，才不会影响最后的实际高度
4. 给子元素的margin-top值改为给父元素 加padding-top，这样就避免了使用margin-top值导致的问题  

[点击查看-给小盒子加margin-top效果示例](https://codepen.io/smileyby/pen/GGeeEG)

* margin负值的使用技巧
> 保持元素的结构不变，改变元素所在的位置
[点击查看-具体效果展示](https://codepen.io/smileyby/pen/rKRRXy)

### paddinghe1margin的区别
* padding是内边距=>会影响我们在浏览器中看到的元素的实际大小，内边距会让元素的内容增大和其他元素没有关系
* margin是外边距=>不会影响我们在浏览器中看到的元素的实际大小，外边距不会让元素的内容增大适合另一个元素的间距

### CSS盒子模型的计算
* 元素的实际宽度 = width + padding-left + padding-right + border-left + border-right
* 元素的实际高度 = height + padding-top + padding-bottom + border-top + border-bottom

**元素的实际大小只会受padding和border的影响**
**如果加了padding或border的值，计算width和height的值是要对应减去，否则内容会溢出**

## CSS 背景相关
###background 背景
* 背景属性说些：可以在一个生命中这是所有的背景属性
* 背景图像支持引入多个图
* 主要属性有：
> background-color 
>> CSS属性中的background-color会设置元素的背景色，属性值为**颜色值**或关键字**transparent**二者选其一
>> [点击查看-背景色示例](https://codepen.io/smileyby/pen/mKgXxr)

> background-image
>> 
* background-image属性用于为一个元素设置一个或多个背景图像。图像在绘制时，以x方向堆叠方式进行。先指定图像会在之后指定的图像上面绘制，因此指定的第一个图像最接近用户。  
* 然后元素的borders会在他们之上被绘制，而`background-color`会在他们之下绘制。图像绘制与盒子以及盒子的边框的关系，需要在`background-clip`和`background-origin`中定义
* 如果一个指定的图像无法被绘制（比如，设定的URI会便是的文件无法加载），浏览器会将此情况等同于其值被设置为none
* 即使图像是不透明的，背景色在通常情况下并不会被显示，web开发者仍然应该指定`background-color`属性。如果图像无法加载-例如在网络连接断开的情况下--背景色就会被绘制。
[点击查看background-image示例](https://codepen.io/smileyby/pen/ERJExx)

> background-repeat 
>> 
>> * background-repeat定义背景图像的重复方式。背景图可以沿着水平轴，垂直轴，两个轴重复，或者根本不重复。
>> * background-repeat 可能的取值：<table>
	<tr>
		<td>单值</td>
		<td>双值</td>
	</tr>
	<tr>
		<td>repeat-x</td>
		<td>repeat no-repeat</td>
	</tr>
	<tr>
		<td>repeat-y</td>
		<td>no-repeat repeat</td>
	</tr>
	<tr>
		<td>repeat</td>
		<td>repeat repeat</td>
	</tr>
	<tr>
		<td>space</td>
		<td>space space</td>
	</tr>
	<tr>
		<td>round</td>
		<td>round round</td>
	</tr>
	<tr>
		<td>no-repeat</td>
		<td>no-repeat no-repeat</td>
	</tr>
</table>
* 在双值语法中，第一个值表示水平重复行为，第二个值表示垂直重复行为。下面是关于每一个值是怎么工作的说明：
<table>
	<tr>
		<td>repeat</td>
		<td>图像会按需重复来覆盖整个背景图片所在的区域，最后一个图像会被剪裁，如果他的大小不合适的话</td>
	</tr>
	<tr>
		<td>space</td>
		<td>图像会尽可能的重复，但是不会剪裁，第一个和最后一个图像会被固定在元素的相应的边上，同时空白会均匀地分布在图像之间 background-position 属性会被忽略，除非只有一个图像能被无建材地显示，只有一种强狂下检查器会发生，那就是图像太大以至于没有足够的空间来完整展示一个图像</td>
	</tr>
	<tr>
		<td>round</td>
		<td>随着允许的空间在尺寸上的增长，被重复的图像将会伸展（没有空隙），直到有足够的空间来添加一个图像，当下一个图像被添加后，所有的当前的图像会被压缩来腾出空间，例如，一个图像原始大小是260px，重复三次之后，可能会被伸展到300px，直到另一个图像被加进来，这样我们就可能被压缩到225px;
</td>
	</tr>
	<tr>
		<td>no-repeat</td>
		<td>图像不会被重复（因为背景图像所在的区域可能没有完全覆盖，那个没有被重复的背景图像的位置由background-position属性来决定</td>
	</tr>
<table>

[点击查看-background-repeat示例](https://codepen.io/smileyby/pen/WyWzZP)

> background-position
>> background-position指定背景图片的初始位置
* 对于每一个被设定的背景图片来说，background-position这个CSS属性设置了一个初始位置。这个初始位置是相对于background-origin定义的背景位置图层（padding-box|border-box|content-box）来说的。（初始值：`0% 0%`）
* 一个值时，对应在取值的位置，另一个方向的位置为居中
* 两个值时，水平和垂直方向按照取值来确定
* 两张背景图片是，规则和上面一样。
```css
/* 关键词取值 */
background-position: top;
background-position: bottom;
background-position: left;
background-position: right;
background-position: center;

/* 百分比取值 */
background-position: 20% 75%;、

/* 长度取值 */
background-position: 0 0;
background-position: 1cm 2cm;
background-position: 10ch 8em;

/* 多张背景图时 */
background-position: 0 0， center;

/* Edge offsets values */
background-position: bottom 10px right 20px;
background-position: right 3em bottom 10px;
background-position: bottom 10px right;
background-position: top right 10px;
/* 全局取值 */
background-position: inherit;
background-position: initial;
background-position: unset;
``` 

[点击查看-效果展示](https://codepen.io/smileyby/pen/MXRPzz)

> background-attachment
>> background-attachment属性决定背景是在视口中固定的还是随包含它的区块滚动。
>>
* 可能的取值：scroll/local/scroll/inherit；
* fixed-此关键字表示内容相对于视口固定。即使一个元素拥有滚动机制，背景也不会随着元素的内容滚动。
* local-此关键字表示背景相对于元素的内容固定。如果一个元素拥有滚动机制，背景将会随着元素的内容滚动，并且背景的绘制区域和定位区域是相对于可滚动区域而不是包含他们的边框
* scroll-此关键字表示背景相对于元素本身固定，而不是随着他的内容滚动（对元素边框是有效的）

[点击查看-效果展示](https://codepen.io/smileyby/pen/OEGrYy)
**三个属性的区别，请在上面网页中自行修改体验。**
 
> background-size
>> 设置背景图大小
>>
* 注意：没有被背景图片覆盖的北京区域仍然会显示用`background-color`属性设置的背景颜色，此外，如果背景图片设置了透明或者半透明属性，臣在背景图片后面的背景色也会显示出来。
* 单张图片的背景大小可以使用：关键词`contain`（缩放背景图片完整装入背景区，可能背景部分空白）或 关键词`cover`（缩放背景图片完全覆盖背景区，可能背景图片部分看不见）或设定宽度和高度
* 当通过宽度和高度来设定尺寸时，你可以提供一或两个数值：如果仅有一个数值被给定，这个数值将作为宽度值大小，高度值将被设定为auto；如果两个数值被给定，第一个将作为宽度值大小，第二个将作为高度值大小。
```css
/* 关键字 */
background-size: cover
background-size: contain

/* 一个值: 这个值指定图片的宽度，图片的高度隐式的为auto */
background-size: 50%
background-size: 3em
background-size: 12px
background-size: auto

/* 两个值 */
/* 第一个值指定图片的宽度，第二个值指定图片的高度 */
background-size: 50% auto
background-size: 3em 25%
background-size: auto 6px
background-size: auto auto

/* 逗号分隔的多个值：设置多重背景 */
background-size: auto, auto     /* 不同于background-size: auto auto */
background-size: 50%, 25%, 25%
background-size: 6px, auto, contain

/* 全局属性 */
background-size: inherit;
background-size: initial;
background-size: unset;
``` 
[点击查看-效果展示](https://codepen.io/smileyby/pen/wXZOPE)
> background-origin
>> background-origin 规定了指定背景图片`background-image`属性的原点位置的背景相对区域
>> 可能的取值：
>>
* border-box 背景图片的摆放以border区域为参考
* padding-box 背景图片的摆放位置以padding、
*区域为参考
* content-box 背景图片的摆放区域以content区域为参考
[点击查看-background-origin效果](https://codepen.io/smileyby/pen/oyOOvp)

**有多张背景图片是，background-origin可以设置为`background-origin: content-box, padding-box;`根据设置来确定原点的位置所在。**
 
> background-clip
>> background-clip 设置元素的背景是否延伸到边框下面
>>
* 如果没有设置背景颜色或图片，那么这个属性只有在边框（border）设置为透明或半透明是才能看到效果，不然的话，这个属性造成的样式变化会被边框遮盖住。
* 可能的取值：
* border-box 背景延伸到边框外延
* padding-box 边框下面没有背景，即背景延伸到内边距外沿
* content-box 背景被剪裁到内容外沿

[点击查看-效果展示](https://codepen.io/smileyby/pen/mKYbOJ)

## overflow:hidden的多种作用
1. overflow 移除隐藏
2. 清除浮动（父元素内的子元素如果浮动，则父元素不能被撑开，使用overflow:hidden;来清除浮动）
3. 解决margin-top的传递问题

[点击查看-效果展示](https://codepen.io/smileyby/pen/NzVjOa)

## 多个元素在一行显示
* display:inline;
* display:inline-block;
* float: left/right;
> 【display:inline-block;元素特点】
> 
* 让盒子横向排列
* vertical-align属性会影响到inline-block元素，你可能会把它的值设置为top
* 你需要设置每一列的宽度
* 如果HTML源代码中元素之间有空格，那么列与列之间会产生间隙

[点击查看-效果示例](https://codepen.io/smileyby/pen/LroLGp)

## 单行文本和单行文本出现省略号的方法
> 单行文本：
> 
>> 单行文本出现省略号的条件：
>
* 容器元素必须要有宽度
* 溢出隐藏（overflow:hidden;）
* 强制文字不折行（white-space:nowrap）
* 文字以省略号方式隐藏（text-overflow:ellipsis）

> 多行文本
> 
>> 多行文本出现省略号的条件：
>
* 弹性盒模型（display:-webkit-box;）
* 规定元素的排列方式：垂直排列 （-webkit-box-orient: vertical）
* 需要显示的文字的行数（-webkit-line-clamp:2）
* 溢出隐藏 （overflow:hidden）
* 
**主要用在移动端手机页面** 

[点击查看-省略号展示效果](https://codepen.io/smileyby/pen/BVedav)

## float浮动
> 浮动元素的特点：
> 
1. 浮动元素在一行显示
2. 设置属性值为left时，浮动元素会一次从父级盒子的左侧项右侧排布，设置属性为right时，浮动元素会一次从父级盒子的右侧向左侧排布
3. 浮动元素自动具有块级元素的属性
4. 浮动元素脱离文档流
5. 浮动元素内的子元素，不会继承浮动属性
6. 浮动元素下面的元素不能识别浮动元素的高度和位置
7. 浮动元素本身具有块元素的特点，所以用了浮动就不需要再加display:block;了[点击查看-示例代码](https://codepen.io/anon/pen/yEWKLx)

## 文档流和脱离文档流
* 文档流：指的是元素排版布局过程中，元素会自动从左到右，从上到下的流式排列。并最终窗体自上而下分成一行行，并在每行中从左到右的顺序排放元素；
* 每个非独董块级元素都独占一行，浮动元素则按照规定在行的一段。若当前行容不下，则另起新行在浮动
* 内联元素也不会独占一行；几乎所有的元素均可生成子行，用于排放子元素
* 标准文档流登记：分为连个，**块级元素** **行内元素**
* 脱离文档流：文档流内的正常元素识别不到这个元素了（脱离文档流的元素相当于平行漂浮在文档流之上）
* 文档流可以分等级：块级元素（从上到下）和行内元素（从左到右）
* 脱离文档流的影响：浮动和定位都可以

## 浮动float
* float可能的取值： left/right/none
> float元素产生的影响：
> 
1. 父元素设置背景色不起作用
2. 父元素设置内边距不会被撑开
3. 父元素设置边框不会被撑开

[点击查看-效果示例](https://codepen.io/smileyby/pen/yEWjMY)

> 清除浮动的方法、
> 
1. 手动设置高度
2. 给浮动元素的父元素设置overflow:hidden/auto
3. 在浮动元素的父元素结束标签之前加一个具有块元素特点的标签（如div），给元素加一个clear:both <div style="clear:both">/div>
4. 利用伪元素:after除浮动

[点击查看-清除浮动效果](https://codepen.io/smileyby/pen/ZRNmrd)

## 如何让元素消失在我们的视野中
1. opacity:0;
2. display: none;
3. visibility: hidden;
4. height:0;和overflow:hidden;
5. line-height:0;和overflow:hidden;（没有设置高度的情况下）
6. margin/padding设置足够大 只要让他消失即可
7. 利用transform属性 让translate坐标设置足够大

## 定位-绝对定位
> 特点：
> 
* 脱离文档流
* 可以设置参照物，参照物必须是其父级元素（直系父级），如果直接父级没有一直往上查找知道找到最外层根元素为止。
* 有宽度和高度的情况下，top和bottom同时存在，top生效，left和right同时存在，left生效
* 没有宽度和高度的情况下，top和bottom同时设置的情况下，会将这个盒子拉大，上下值都起作用，左右同理
* 可以设置层级关系z-index属性 
* 相对参照物只要是定位元素就可以（绝对定位 相对定位 固定定位），优先选择相对定位（position:relative;）
=> 绝对定位和固定定位 都会脱离文档流 不占位

**注意：绝对定位一定要给他相对参照物，绝对定位一定要指明它定位的方向**

## 定位-相对定位
> 相对定位特点：
> 
* 不会脱离文档流
* 可以设置上下左右四个方位属性
* 如果同时设置 left和right，left生效；同时设置top和bottom bottom生效
* 参照物就是自己本身
* 可以设置z-index属性，z-index属性越大越在上

**注意：z-index必须要和定位元素配合才能生效（absolute relative fixed）**

## 定位-固定定位
> 固定定位特点：
> 
* 脱离文档流
* 参照物是浏览器的可视窗口
* 任何元素都可以设置固定定位，同时设置left/right left生效；同时设置top/bottom top生效
* 可以设置top/left/bottom/right四个方位
* 可以通过z-index来改变层级

### z-index的特点
* 默认是书写顺序在后的定位元素覆盖在顺序在前的定位元素
* 可以使用z-index属性修改定位元素的层级关系
* z-index值的数字没有单位，支持负数
* 一般都是统计元素进行层级的比较
* 当参照物是相对定位或绝对定位的时候，父级元素之间没有z-index值，子元素的z-index值会出来作比较；


## 参考链接
[CSS 参考](https://developer.mozilla.org/zh-CN/docs/Web/CSS/Reference)




## HTML基本结构 - 文档声明

* 为了说明文档使用的超文本标记语言，所有超文本标记语言文档应该以“文件类型声明”（外语全称加缩写<!DOCTYPE>）开头，引用一个文件类型或者必要情况下自定义一个文件类型描述。
* <!DOCTYPE>声明必须是HTML文档的第一行，位于<html>标签之前
* <!DOCTYPE>声明不是HTML标签；它是web浏览器关于页面使用那个HTML版本进行编译的指令。
* 在HTML4.01中，<!DOCTYPE>声明引用DTD，因为HTML4.01基于SGML。DTD规定了标记语言的规则，这样浏览器才能正确地呈现内容。
* HTML5不基于SGML，所以不需要引用DTD。

> [SGML百度百科]((https://baike.baidu.com/item/%E6%A0%87%E5%87%86%E9%80%9A%E7%94%A8%E7%BD%AE%E6%A0%87%E8%AF%AD%E8%A8%80/10471466?fr=aladdin&fromid=2901416&fromtitle=SGML))
> 
> [dtd百度百科](https://baike.baidu.com/item/dtd/2661276?fr=aladdin)

```html

<!-- html4示例 -->
<!DOCTYPE HTML PUBLIC "-//W3C//DTD HTML 4.01 Transitional//EN"
        "http://www.w3.org/TR/html4/loose.dtd">
<html>
<head>
    <title>Title</title>
</head>
<body>

</body>
</html>

<!-- html5示例 -->
<!DOCTYPE html>
<html lang="en">
<head>
    <meta charset="UTF-8">
    <title>Title</title>
</head>
<body>

</body>
</html>




```

## HTML基本结构 - head

* <head>标签用于定义文档的头部，它是所有头部元素的容器。
* <head>中的元素可以引用脚本，指示浏览器在哪里找到样式表、提供元信息等等。
* 文档的头部描述了文档的各种属性和信息，包括文档的标题、在web中的位置以及和其他文档的关系等。绝大多数文档头部包含的数据都不会真正作为内容显示给用户。
* 下面这些标签可用在head部分：<link>,<meta>,<script>,<style>,以及<title>

## HTML基本结构 - title

* <title>定义文档的标题，它是head部分中唯一必须的元素
* 一定要选择一个正确的标题，这对于定义文档并确保能够在Web上有效利用来说是十分重要的。
* 显示在浏览器的页槛位置。

## HTML基本结构 - meta

* <meta>标签提供关于HTML文档的元数据。元数据不会显示在页面上，但是对于手机可读；
* 典型的情况，meta元素被用于规定页面的描述、关键词、文档的作者、最后修改时间以及其他元数据；
* 关于meta的标签属性；（必需的属性）

## HTML基本结构 - body

* 网页的主体部分
* body 元素定义文档的主体，用户看到的内容基本都在body内编写。
* body 元素包含文档的所有内容（比如文本、超链接、图像、表格和列表等等。）
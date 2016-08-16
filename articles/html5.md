# 
- <template>标签自带display:none，2. 标签位置任意性
除了上面<template>子元素天然隐藏外，<template>标签还有一个特性，就是位置任意性，这非常类似<script>或者<style>标签，可以在<head>中，也可以在<body>或者<frameset>中。

3. childNodes无效性
虽然，肉眼看上去是<template>标签里面还有很多子标签，这种惯性思维在这里是不受用的。假设变量template是我们获得的一个<template>标签DOM（里面一大堆HTML代码），你会发现：template.childNodes是个空大屁。我们可以使用template.innerHTML获取完整的HTML片段。如果你非得获取“伪子元素”。也是有办法的，OK，睁大眼睛，要使用content属性。

template.content会返回一个文档片段，你可以理解为另外一个document，然后，使用document下的一些查询API就可以获得<template>标签里面的“伪子元素”了。例如，获得第一张图片元素则是：

var image_first = template.content.querySelector("img");
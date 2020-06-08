---
title: "HTML常用标签"
date: 2020-06-08T20:17:47+08:00
draft: false
---

## 一、a 标签的用法

1. **定义**：定义超链接，从一个页面跳向另一个页面
2. **常用的属性**：

   a. href：规定跳转指向的 URL

   b. target：设置跳转方式

   c. dowload：规定被下载的目标

   d. rel=noopener：防止 JS 中 window.opener 引发 的安全问题

3. **作用**：

- _跳转到外部网址_

  1.https 协议地址，例如**https://www.baidu.com**

  2.http 协议地址，例如**http://www.baidu.com**

  3.不加协议，会自动选择适用协议，例如 **//www.baidu.com**

- _跳转到内部锚点的路径_

  1.绝对路径，例如 **/a/b/c**，/a 即开启 http 服务的根目录；相对路径**a/b/c**，相对当前目录

  2.指向某个文件：例如 **index.html** , **./index.html**

* _跳转到邮箱或电话等伪协议_

  1. javascript 代码，例如

  ```
  **<a href="javascript: ; ">js</a>**
  ```

  2. id：#xxx；跳转到对应的 id 选择器
  3. mailto：邮箱；

  ```
  <a href="mailto:111@qq.com">发邮箱</a>
  ```

  4. tel：手机号

  ```
  < a href="tel: 111111">发邮箱</a>
  ```

4. **target**

- **内置名字**

\_blank：在新页面打开

\_top：在最顶层窗口打开指定页面

\_parent：父级窗口打开指定页面

\_self：当前页面，默认值

\_ 设置为指定名字 xx：会覆盖已打开名为 xx 的页面

- **程序命名**
  - window 的 name：开发者工具查看当前 tab 的 name
  - iframe 的 name：在指定 iframe 打开 a 标签链接

## 二、img 标签

1. 作用：发出 get 请求，并展示一张图片
2. 属性：

   （1）alt：加载失败时显示的图片

   （2）height：宽

   （3）width：高

   （4）src：指定图片

3. 事件：onload/onerror：监听图片是否加载成功

```
<script>
    xx.onload = function(){
        console.log("图片加载成功");
    };
    xx.onerror = function(){
        console.log("图片加载失败");
        xx.src = "/404.png";
    };
</script>
```

4. 响应式：max-width：100%：自适应手机端
5. 可替换元素：CSS 可以影响可替换元素的位置，但不会影响到可替换元素自身的内容。

## 三、table 表格的用法

1. 基本结构

```
<table>
    <thead></thead>
    <tbody></tbody>
    <tfoot></tfoot>
</table>
```

2. 标签

   1）thead：包含 tr 行元素，tr 包含 th 表头

   2）tbody：里面有 tr 行元素，tr 可以包含**th 表头**和**td 表数据**

   3）tfoot：表尾，不会根据代码位置而改变表尾在表格中的位置

3. 样式

   1）table-layout：auto；定义表格布局的算法，常用 auto 为自动根据内容来计算宽度，fixed 固定宽度；

   2）border-cllapse：collapse；合并表格间隙

   3）border-spacing：0；表格的间隙宽度

---
layout: post
title: "加入 LaTeX 公式支持"
date: 2015-04-28
comments: true
categories: update
tag: 
  - LaTeX 
  - kramdown
---
[MathJax][5] 实在是一个很好的网页 $$\LaTeX$$ 解决方案。

## 鸣谢

参考了这两个博客：

1. [Jekyll中使用MathJax][1]

2. [Octopress中使用 $$\LaTeX$$ 写数学公式][2]

## 设置

### 第一步 修改`_config.yml`文件

将 markdown 引擎设置为 kramdown:

~~~
markdown: kramdown
~~~

本地使用 Jekyll 时可能需要额外安装 kramdown:

~~~
gem install kramdown
~~~

### 第二步 在 header 中添加 MathJax 的 Javascript 代码

即，在`_layouts/default.html`里的`<head>`与`</head>`之间加入一下代码：

~~~ html
<script type="text/javascript"
  src="https://cdn.mathjax.org/mathjax/latest/MathJax.js?config=TeX-AMS-MML_HTMLorMML">
</script>
~~~

**设置完成！**

## 使用方法

一句话：用两个美元符号`$$`在前后把公式包起来就行了。

这里需要注意与 $$\LaTeX$$ 不同的是，这里不论行内还是行间都是`$$`。

## 示例：

~~~ latex
$$E=mc^2$$ is a inline formula.
~~~

$$E=mc^2$$ is a inline formula.

### Schrödinger 方程
~~~ latex
$$
\left [ – \frac{\hbar^2}{2 m} \frac{\partial^2}{\partial x^2} + V \right ] \Psi = i \hbar \frac{\partial}{\partial t} \Psi
$$
~~~

$$
\left [ – \frac{\hbar^2}{2 m} \frac{\partial^2}{\partial x^2} + V \right ] \Psi = i \hbar \frac{\partial}{\partial t} \Psi
$$

### Lorentz 方程 

~~~ latex
$$ 
\begin{aligned} \dot{x} &= \sigma(y-x) \\ 
\dot{y} &= \rho x - y - xz \\ 
\dot{z} &= -\beta z + xy \end{aligned} 
$$
~~~

$$ 
\begin{aligned} \dot{x} &= \sigma(y-x) \\ 
\dot{y} &= \rho x - y - xz \\ 
\dot{z} &= -\beta z + xy \end{aligned} 
$$

### Cauchy-Schwarz 不等式 

~~~ latex
$$ 
\left( \sum_{k=1}^n a_k b_k \right)^2 \leq \left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right)
$$
~~~

$$ 
\left( \sum_{k=1}^n a_k b_k \right)^2 \leq \left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right)
$$

### 某种诡异的叉乘公式

~~~ latex
$$
\mathbf{V}_1 \times \mathbf{V}_2 =  \begin{vmatrix} \mathbf{i} &\mathbf{j} &\mathbf{k} \\ 
\frac{\partial X}{\partial u} &  \frac{\partial Y}{\partial u} & 0 \\ 
\frac{\partial X}{\partial v} &  \frac{\partial Y}{\partial v} & 0 \end{vmatrix} 
$$
~~~

$$
\mathbf{V}_1 \times \mathbf{V}_2 =  \begin{vmatrix} \mathbf{i} &\mathbf{j} &\mathbf{k} \\ 
\frac{\partial X}{\partial u} &  \frac{\partial Y}{\partial u} & 0 \\ 
\frac{\partial X}{\partial v} &  \frac{\partial Y}{\partial v} & 0 \end{vmatrix} 
$$

### 二项概率分布(抛$$n$$次硬币出现$$k$$次头的概率)

~~~ latex
$$ 
P(E)   = {n \choose k} p^k (1-p)^{ n-k} 
$$
~~~

$$ 
P(E)   = {n \choose k} p^k (1-p)^{ n-k} 
$$

### Ramanujan 恒等式

~~~ latex
$$ 
\frac{1}{\Bigl(\sqrt{\phi \sqrt{5}}-\phi\Bigr) e^{\frac25 \pi}} 
= 1+\frac{e^{-2\pi}} {1+\frac{e^{-4\pi}} {1+\frac{e^{-6\pi}} 
    {1+\frac{e^{-8\pi}} {1+\ldots} } } } 
$$
~~~

$$ 
\frac{1}{\Bigl(\sqrt{\phi \sqrt{5}}-\phi\Bigr) e^{\frac25 \pi}} 
= 1+\frac{e^{-2\pi}} {1+\frac{e^{-4\pi}} {1+\frac{e^{-6\pi}} 
    {1+\frac{e^{-8\pi}} {1+\ldots} } } } 
$$

### Rogers-Ramanujan 恒等式

~~~ latex
$$ 
1 +  \frac{q^2}{(1-q)}+\frac{q^6}{(1-q)(1-q^2)}+\cdots =
\prod_{j=0}^{\infty}\frac{1}{(1-q^{5j+2})(1-q^{5j+3})},
    \quad\quad \text{for $|q|<1$} 
$$
~~~

$$ 
1 +  \frac{q^2}{(1-q)}+\frac{q^6}{(1-q)(1-q^2)}+\cdots =
\prod_{j=0}^{\infty}\frac{1}{(1-q^{5j+2})(1-q^{5j+3})},
    \quad\quad \text{for $|q|<1$} 
$$

### Maxwell 方程

~~~ latex
$$
\begin{aligned} \nabla \times \vec{\mathbf{B}} -\, \frac1c\, \frac{\partial\vec{\mathbf{E}}}{\partial t} & = \frac{4\pi}{c}\vec{\mathbf{j}} \\   
\nabla \cdot \vec{\mathbf{E}} & = 4 \pi \rho \\ 
\nabla \times \vec{\mathbf{E}}\, +\, \frac1c\, \frac{\partial\vec{\mathbf{B}}}{\partial t} & = \vec{\mathbf{0}} \\ 
\nabla \cdot \vec{\mathbf{B}} & = 0 \end{aligned} 
$$
~~~

$$
\begin{aligned} \nabla \times \vec{\mathbf{B}} -\, \frac1c\, \frac{\partial\vec{\mathbf{E}}}{\partial t} & = \frac{4\pi}{c}\vec{\mathbf{j}} \\   
\nabla \cdot \vec{\mathbf{E}} & = 4 \pi \rho \\ 
\nabla \times \vec{\mathbf{E}}\, +\, \frac1c\, \frac{\partial\vec{\mathbf{B}}}{\partial t} & = \vec{\mathbf{0}} \\ 
\nabla \cdot \vec{\mathbf{B}} & = 0 \end{aligned} 
$$

## 多余的话

在 Mathjax 的[官方文档][3]里也有对行间公式表示方法的说明，上面的第一个博客使用了 Mathjax 不太推荐的方案，即启用了`$...$`单美元符号，<del>我可能考虑在以后去掉这一做法</del>我去掉了，使用了默认的设置，即不管行内还是行间都是用**双美元符号**(`$$...$$`)表示公式。

<del>还有，我基本按照第一篇博客的方法，但发现我的`_include/`路径下并没有`header.html`文件，我就自己创建了一个，并在`_layout/post.html`里 include 了`header.html` ，然后就可以显示了。</del>

<del>不过感觉这样的做法有点怪异，过几天考虑把`header.html`里的代码放到`_include/defult.html`里面。</del>

## <del>问题</del>

现在主要的问题就是公式的字体太小，我的 html 知识实在不够，自己审查元素看了一下，发现对于行间公式的显示，*我的电脑*的浏览器上，会出现一个`element.style`，并有`font-size:50%`；行内公式也有`element.style`，但却是`font-size:116%`，我没有在 jekyll 的 css 文件里找到相应的代码。更奇怪的是，在华仔的电脑[^1]上的行间公式却是`font-size:106%`。没搞懂。

还有一个问题就是公式里的字母和符号莫名其妙成为了绿色而数字是黑色，我看其他人的博客一般就都是黑色。我有点怀疑是`highlight.css`文件造成的，但是还没有仔细看其代码。

-----

[^1]: MacBook Pro, Chrome

[1]: http://www.pkuwwt.tk/linux/2013-12-03-jekyll-using-mathjax/ "Jekyll中使用MathJax"
[2]: http://dreamrunner.org/blog/2014/03/09/octopresszhong-shi-yong-latexxie-shu-xue-gong-shi/ "Octopress中使用Latex写数学公式"
[3]: http://docs.mathjax.org/en/latest/start.html
[4]: http://chenminhua.github.io
[5]: http://www.mathjax.org

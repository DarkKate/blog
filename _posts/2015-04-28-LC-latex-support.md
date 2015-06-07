---
layout: post
title: "加入 LaTeX 公式支持"
date: 2015-04-28
comments: true
categories: update LC
tag: 
  - LaTeX 
  - kramdown
---
## 改动

参考了这两个博客：

1. [Jekyll中使用MathJax][1]

2. [Octopress中使用Latex写数学公式][2]

在 Mathjax 的[官方文档][3]里也有对行间公式表示方法的说明，上面的第一个博客使用了 Mathjax 不太推荐的方案，即启用了`$...$`单美元符号，我可能考虑在以后去掉这一做法。

还有，我基本按照第一篇博客的方法，但发现我的`_include/`路径下并没有`header.html`文件，我就自己创建了一个，并在`_layout/post.html`里 include 了`header.html` ，然后就可以显示了。

不过感觉这样的做法有点怪异，过几天考虑把`header.html`里的代码放到`_include/defult.html`里面。

## 问题

现在主要的问题就是公式的字体太小，我的 html 知识实在不够，自己审查元素看了一下，发现对于行间公式的显示，*我的电脑*的浏览器上，会出现一个`element.style`，并有`font-size:50%`；行内公式也有`element.style`，但却是`font-size:116%`，我没有在 jekyll 的 css 文件里找到相应的代码。更奇怪的是，在华仔的电脑[^1]上的行间公式却是`font-size:106%`。没搞懂。

还有一个问题就是公式里的字母和符号莫名其妙成为了绿色而数字是黑色，我看其他人的博客一般就都是黑色。我有点怀疑是`highlight.css`文件造成的，但是还没有仔细看其代码。

## 示例：

$$E=mc^2$$ is a inline formula

### Lorentz方程 

$$ 
\begin{aligned} \dot{x} &= \sigma(y-x) \\ 
\dot{y} &= \rho x - y - xz \\ 
\dot{z} &= -\beta z + xy \end{aligned} 
$$

### Cauchy-Schwarz不等式 

$$ 
\left( \sum_{k=1}^n a_k b_k \right)^2 \leq \left( \sum_{k=1}^n a_k^2 \right) \left( \sum_{k=1}^n b_k^2 \right)
$$

### 某种诡异的叉乘公式

$$
\mathbf{V}_1 \times \mathbf{V}_2 =  \begin{vmatrix} \mathbf{i} &\mathbf{j} &\mathbf{k} \\ 
\frac{\partial X}{\partial u} &  \frac{\partial Y}{\partial u} & 0 \\ 
\frac{\partial X}{\partial v} &  \frac{\partial Y}{\partial v} & 0 \end{vmatrix} 
$$

### 二项概率分布(抛$$n$$次硬币出现$$k$$次头的概率)

$$ 
P(E)   = {n \choose k} p^k (1-p)^{ n-k} 
$$

### Ramanujan恒等式

$$ 
\frac{1}{\Bigl(\sqrt{\phi \sqrt{5}}-\phi\Bigr) e^{\frac25 \pi}} 
= 1+\frac{e^{-2\pi}} {1+\frac{e^{-4\pi}} {1+\frac{e^{-6\pi}} 
    {1+\frac{e^{-8\pi}} {1+\ldots} } } } 
$$

### Rogers-Ramanujan恒等式

$$ 
1 +  \frac{q^2}{(1-q)}+\frac{q^6}{(1-q)(1-q^2)}+\cdots =
\prod_{j=0}^{\infty}\frac{1}{(1-q^{5j+2})(1-q^{5j+3})},
    \quad\quad \text{for $|q|<1$} 
$$

### Maxwell方程

$$
\begin{aligned} \nabla \times \vec{\mathbf{B}} -\, \frac1c\, \frac{\partial\vec{\mathbf{E}}}{\partial t} & = \frac{4\pi}{c}\vec{\mathbf{j}} \\   
\nabla \cdot \vec{\mathbf{E}} & = 4 \pi \rho \\ 
\nabla \times \vec{\mathbf{E}}\, +\, \frac1c\, \frac{\partial\vec{\mathbf{B}}}{\partial t} & = \vec{\mathbf{0}} \\ 
\nabla \cdot \vec{\mathbf{B}} & = 0 \end{aligned} 
$$

-----

[^1]: MacBook Pro, Chrome

[1]: http://www.pkuwwt.tk/linux/2013-12-03-jekyll-using-mathjax/ "Jekyll中使用MathJax"
[2]: http://dreamrunner.org/blog/2014/03/09/octopresszhong-shi-yong-latexxie-shu-xue-gong-shi/ "Octopress中使用Latex写数学公式"
[3]: http://docs.mathjax.org/en/latest/start.html
[4]: http://chenminhua.github.io

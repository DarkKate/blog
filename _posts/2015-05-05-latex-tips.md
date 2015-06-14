---
layout: post
title: "LaTeX Tips"
date: 2015-05-05
comments: true
categories: 学习
tag: 
  - LaTeX
---

## 备忘

写这个主要就是一个备忘的作用，$$\LaTeX$$ 的细节很多，一段时间没用就很容易忘了。上个月就吃到了这个苦头，原来看过的东西没做一个记录，忘了就得重新再查资料，然后在茫茫的信息海洋中寻找我需要的那个知识点，当然有一些问题在网络上也有人问，可以 Google 到，但有的细节还是只有 $$\LaTeX$$ 书籍或文档里才有，还有一个问题就是使用 $$\LaTeX$$ 进行中文排版的方案随着技术的发展出现了好几个解决方案，有时候真的挺晕的。

## Tips

下面想到什么写什么，以后也会慢慢补充。

1. 在独立公式中插入汉字：mbox{汉字}，text{汉字}

2. Tex Live 的 CTeX 模式的默认格式文件在这个目录：D:\texlive\2013\texmf-dist\tex\latex\ctex\cfg\ctexcap.cfg

5. [Jekyll中使用MathJax][1]

6. 中文排版最简单方案，安装 TeX Live 使用 CTeX + XeLaTeX：\documentclass{ctexart}

3. [国标引文格式][2]：\bibliographystyle{gbt7714-2005}

4. 大括号分类图，使用 case 环境。\smash[],t,b 分别指忽略盒子的高度，深度。例如：

$$
\text{锂离子电池电解质}
\begin{cases}
  \strut\smash[t]{\text{液体电解质}
    \begin{cases}
      \text{无机液体电解质} \\
      \text{有机液体电解质}
    \end{cases}}\\
  \text{固体电解质}
    \begin{cases}
      \text{无机固体电解质} \\
      \strut\smash[b]{\text{有机固体电解质}
         \begin{cases}
         \text{纯固体聚合物电解质}\\
         \text{胶体聚合物电解质}
         \end{cases}}\\
    \end{cases}\\
  \text{熔融盐电解质}
\end{cases}
$$


[1]: http://www.pkuwwt.tk/linux/2013-12-03-jekyll-using-mathjax/
[2]: https://github.com/Haixing-Hu/GBT7714-2005-BibTeX-Style

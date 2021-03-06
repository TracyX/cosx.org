---
title: 闲扯“自由度”
date: '2008-12-04T01:20:43+00:00'
author: 胡荣兴
categories:
  - 统计推断
tags:
  - 参数估计
  - 自由度
slug: degrees-of-freedom
forum_id: 418751
---

“闲扯”是一个四川方言词汇，指的就是大家在没事的时候坐下来吹吹牛，聊聊天。现在正是夜深人静的时候，找人聊聊天是不合适的，就由我一个人来自言自语下什么是自由度。

我们进行统计分析，就像一个摄影师在拿着镜头在记录世界。但这个摄影师如果用的是广角镜头，那么他将面临一个问题：几何失真。特别是拍近景的时，拍出来的直线是弯曲的。这样就没有真失地反映客观事物的图像。所以这个时候他的反映真实客观现实的“自由”被限制了。虽然他的自由被限制了，但摄影师还是有办法矫正照的几何失真的：他可以尽量避免用广角镜头拍近景；他可以将照片交给专业的图像处理软件修复。所以，这个摄影师是有很多“自由”的手段来矫正照片失真的问题。这就可以当作是自由度的一个不恰当的类比。

<!--more-->

# 第一次解释

很多时候，在做数据分析时，我们会和上面那个摄影师一样，遇到抽取的样本失真的问题。假设现在有一个总体｛1,2,3,4,5,6,7,8,9｝，其均值为5，我们从这个总体中抽取了一个样本｛3，6，4，7，9｝根据这个样本的均值来估计总体的均值。但样本的均值为5.8，明显高于实际的总体的均值。要想我们抽出的样本达到理想的效果，我们应当是抽取了9，就应当抽取1，抽取了2，就抽取了8。但在我们前面抽取的样本中抽了一个9，却没有1，我们可以重新抽取剩下的个体，让它们中的一个个体值为1，这样我们就有4次机会修正样本与总体不符的问题，这个时候，我们的自由度就是4。

# 第二次解释

上面我们是从背面看到的自由度，现在我们换一个面来看自由度。还是上面的那个总体，现在我从中抽取了一个样本｛x，6，4，7，9｝,我现在告诉你，抽出的样本的均值为5.8，那么x的值是多少？我们很容易就得到答案：3。为什么我们能知道它是3呢？是因为这个3它不是独立的。它是与样本均值相联系的。这时，失去了一个自由度，此时自由度应当是4。

再来看线性回归模型

`$$
Y_i = a + bx_i + \epsilon_i
$$`
的残差
`$$
e_i = y_i - (\hat{a}+\hat{b}x_i)
$$`
它受到下面两个条件限制
`$$
\begin{align*}
& e_{1}+\ldots +e_{n}=0\\
& x_{1}e_{1}+\ldots +x_{n}e_{n}=0
\end{align*}
$$`

所以它失去了两个自由度，误差的自由度为n-2。

# 第三次解释

从它外表的两个方面看清楚什么是自由度了么？下面我们来挖地三尺，到内部去看看。

从几何上看，自由度可以看作是向量空间的维数。

假设我们有一个样本，有n个观测，它们来自n个独立的正态总体。该样本可以看作是一个n维随机向量：
`$$
\left(
  \begin{matrix}
   x,\\ \vdots \\ x_{n}
   \end{matrix}
  \right)
$$`

它来自n维空间，所以它的自由度为n.

设`\(\overline {x}\)`为样本均值，我们可以对样本作如下分解：

`$$
\left(
  \begin{matrix} x\\ :\\ x_{n}
  \end{matrix}
\right)
=\overline {x}
\left(
  \begin{matrix}
  1\\ \vdots \\ 1
  \end{matrix}
\right) +
\left(
  \begin{matrix}
  x_{1}-\overline {x}\\ \vdots\\ x_{n}-\overline {x}
  \end{matrix}
\right)
$$`

等式右边第一个向量空间的自由度为1,第二个向量受条件`\(\sum _{i=1}^{n}\left( x_{i}-\overline {x}\right) =0\)`限制，它的自由度为n-1。

从数学上看，等式右边的第一个向量可以看作是等号左边向量在由1‘张成的子空间上的最小二乘（或正交）投影，该子空间的维数为1，所以它的自由度也是1；等式右边第二个向量可以看作是等式左边向量在（n-1)维正交补空间上的最小二乘投影，所以自由度为n-1

统计学上的样本离差平方和可以看作是上等式右边第二个向量的模：
`$$
\sum _{i=1}^{n}
\left(
  x_{i}-x
\right) ^{2}=
\left\|
  \begin{matrix}
    x,-\overline {x}\\
    \vdots\\
    x_{n}-\overline {x}
    \end{matrix}
\right\| ^{2}
$$`

所以由它导出的统计量`\(\dfrac {nS^{2}} {\sigma^{2}}\)` 服从自由度为n-1的卡方分布。

# 第四次解释

该你来做了噻。

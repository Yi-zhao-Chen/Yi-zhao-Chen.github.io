---
layout: post
title: A Collection of Baker-Campbell-Hausdorff-Type formulas(In Chinese)
date: 2025-05-09 23:25:16
description: A collection of formulas similar to Baker-Campbell-Hausdorff formula and their proofs (which are simpler than that of BCH formula).
tags:
categories: Notes
toc:
  beginning: true
---

在李群和李代数的理论中，一个比较重要的公式是Baker-Campbell-Hausdorff公式（BCH公式，也称Dynkin公式）：

> **定理**：任给李群$$G$$，记它的李代数$$\mathfrak{g}$$，则存在$$\mathfrak{g}$$在$$0$$处的邻域$$U$$，使得对任意的$$X,Y \in U$$，有下面的等式：
>
> $$
> \exp(X)\exp(Y) = \exp(Z)
> $$
>
> 其中$$Z$$可表示为关于$$X,Y$$的李括号和高阶李括号的无穷级数。具体而言，有：
>
> $$
> \begin{aligned}
>   Z & = X+Y+\frac{1}{2}[X,Y]+\cdots \\
>   & = X + Y + \sum_{k=1}^{+\infty} \frac{(-1)^k}{k+1} \sum \frac{(-1)^{\sum_i (l_i + m_i)}}{l_1 + \cdots + l_k + 1} \frac{(\operatorname{ad}_Y)^{l_1}}{l_1!} \circ \frac{(\operatorname{ad}_X)^{m_1}}{m_1!} \circ \cdots \circ \frac{(\operatorname{ad}_Y)^{l_k}}{l_k!} \circ \frac{(\operatorname{ad}_X)^{m_k}}{m_k!} (Y) \\
> \end{aligned}
> $$
>
> 这里第二个求和号是对所有的整数$$l_1,\dots,l_k,m_1,\dots,m_k\geqslant 0, m_i+l_i >0$$求和。

BCH公式是一个相当一般的结果，但很多时候我们不需要用到这么强的结论，比如只需要给出一阶展开或者二阶展开就足够了，在这个时候，对应的结论也会有更简单的证明。在这篇笔记里，我们将这些更弱的结论称作Baker-Campbell-Hausdorff型(BCH型)的公式。而这篇笔记的目的就是记录一些BCH型的公式及其证明。

这篇笔记里给出的公式都可以由BCH公式推出，但我们会给出独立于BCH公式的证明。对于BCH型的公式，一个相当诱人的证明方式是，将$$\exp(X)$$展开为无穷级数来计算（事实上，不少资料里，矩阵李群的BCH公式就是用这种办法证明的）。这一办法对于矩阵李群可行，但不适用于一般的李群。这篇笔记中展示的证明都是一般李群上的证明。

---

在开始之前，我们不加证明地给出一些基本的概念和结论。

对一个李群$$G$$，我们用对应的哥特体小写字母$$\mathfrak{g}$$表示它的李代数，比如向量空间$$V$$上的线性变换群$$GL(V)$$的李代数为$$\mathfrak{gl}(V)$$. 我们用$$\operatorname{Ad}$$表示$$G$$在$$\mathfrak{g}$$上的伴随作用：

$$
\begin{aligned}
    \operatorname{Ad} \colon G & \longrightarrow GL(\mathfrak{g}) \\
    g & \longmapsto \operatorname{Ad}_g \\
\end{aligned}
$$

我们之后会用到的伴随作用$$\operatorname{Ad}$$的性质是

$$
g\exp(X)g^{-1} = \exp(\operatorname{Ad}_gX),\; \forall g\in G, X\in\mathfrak{g}.
$$

伴随作用的切映射给出的是$$\mathfrak{g}$$在$$\mathfrak{g}$$上的伴随作用

$$
\operatorname{ad}\colon X \mapsto \operatorname{ad}_X.
$$

根据指数映射的自然性，我们有$$\operatorname{Ad}_{\exp(X)} = e^{\operatorname{ad}_X}$$，也就是下面的交换图：

$$
\begin{array}{rcl}
    G & \longrightarrow &  GL(\mathfrak{g}) \\
    \exp\uparrow & & \uparrow e^{A} \\
    \mathfrak{g} & \longrightarrow & \mathfrak{gl}(\mathfrak{g}) \\
\end{array}
$$

我们最后指出，$$\operatorname{ad}$$就是李括号，也就是

$$
\operatorname{ad}_X Y = [X,Y],\quad \forall X,Y \in \mathfrak{g}.
$$

下面进入到对具体公式的讨论。

## $$\exp(sX)\exp(tY)\exp(-sX)$$的展开

一个相当简单的例子是$$\exp(sX)\exp(tY)\exp(-sX)$$的展开。我们可以相当容易地给出任意阶展开：

$$
\begin{aligned}
    \exp(sX)\exp(tY)\exp(-sX)
    & = \exp\left(t(Y+s[X,Y]+\frac{s^2}{2}[X,[X,Y]]+\cdots)\right) \\
    & = \exp\left(t\sum_{n=0}^{\infty}\frac{s^n}{n!}(\operatorname{ad}_{X})^{n}Y\right) \\
\end{aligned}
$$

---

事实上，利用前面给出的基本性质，有

$$
\begin{aligned}
    \exp(sX)\exp(tY)\exp(-sX)
    & = \exp\left(\operatorname{Ad}_{\exp(sX)}(tY)\right)\\
    & = \exp\left(t\cdot e^{\operatorname{ad}_{sX}}Y\right)\\
    & = \exp\left(t\cdot\sum_{n=0}^{+\infty} \frac{s^n}{n!}(\operatorname{ad}_X)^{n}Y\right) \\
    & = \exp\left(t(Y+s[X,Y]+\frac{s^2}{2}[X,[X,Y]]+\cdots)\right) \\
\end{aligned}
$$

上面的等式里，如果令$$s=t$$，还可以得到$$\exp(tX)\exp(tY)\exp(-tX)$$的二阶展开：

$$
\exp(tX)\exp(tY)\exp(-tX)=\exp(tY+t^2[X,Y]+O(t^3)).
$$

## $$\exp(tX)\exp(sY)\exp(-tX)\exp(-sY)$$的二阶展开

另一个可能会碰到的例子是

$$
\exp(tX)\exp(sY)\exp(-tX)\exp(-sY) = \exp(st[X,Y]+o(s^2+t^2))
$$

如果在上面的公式里取$$s=t$$，就会得到

$$
\exp(tX)\exp(tY)\exp(-tX)\exp(-tY) = \exp(t^2[X,Y]+o(t^2))
$$

这说明李代数的李括号和李群的交换子是几乎对应的。

---

我们下面证明第一个公式。这可以靠计算

$$
F(s,t) \colon= \exp^{-1}(\exp(tX)\exp(sY)\exp(-tX)\exp(-sY))
$$

在$$(0,0)$$处的前两阶偏导数得到。我们给出具体的计算。

从$$F(s,t)$$的表达式可以看出的是

$$
F(0,t)=F(s,0)=0 \in \mathfrak{g},\; \forall s,t\in \mathbb{R}
$$

由此可以知道：

$$
\begin{aligned}
    \frac{\partial F}{\partial t}(0,0) = \frac{\partial F}{\partial s}(0,0) = 0 \\
    \frac{\partial^2 F}{\partial t^2}(0,0) = \frac{\partial^2 F}{\partial s^2}(0,0) = 0 \\
\end{aligned}
$$

又有

$$
\begin{aligned}
    \frac{\partial F}{\partial s}(0,t) & = \frac{\mathrm{d}}{\mathrm{d}s}\Big\vert_{s=0} \exp^{-1}(\exp(tX)\exp(sY)\exp(-tX)\exp(-sY)) \\
    & = \frac{\mathrm{d}}{\mathrm{d}s}\Big\vert_{s=0} \exp^{-1}(\exp(s\cdot\operatorname{Ad}_{\exp(tX)}Y)\exp(-sY)) \\
    & = \exp^{-1}_{*}\big\vert_{e}\left(\operatorname{Ad}_{\exp(tX)}Y + (-Y)\right) \\
    & = \operatorname{Ad}_{\exp(tX)}Y -Y \\
\end{aligned}
$$

所以再进一步对$$t$$求导可得：

$$
\begin{aligned}
    \frac{\partial^2F}{\partial t\partial s}(0,0)
    & = \frac{\mathrm{d}}{\mathrm{d}t}\Big\vert_{t=0}(\operatorname{Ad}_{\exp(tX)}Y - Y) \\
    & = \operatorname{ad}_X Y = [X,Y].
\end{aligned}
$$

这样我们可以得到$$F(s,t)$$的二阶展开

$$
\begin{aligned}
    F(s,t) = & F(0,0)+\frac{\partial F}{\partial t}(0,0)\cdot t + \frac{\partial F}{\partial s}(0,0)\cdot s \\
    & + \frac{1}{2}\left(\frac{\partial^2 F}{\partial t^2}(0,0)\cdot t^2 +2 \frac{\partial^2 F}{\partial t\partial s}(0,0) \cdot st + \frac{\partial^2 F}{\partial s^2}(0,0)\cdot s^2\right) \\
    & + o(s^2+t^2) \\
    = & st [X,Y] + o(s^2+t^2) \\
\end{aligned}
$$

在上面等式的两边作用指数映射，就得到了这一节开头的公式。

## $$\exp(tX)\exp(sY)$$的二阶展开

我们在这一节里给出$$\exp(tX)\exp(tY)$$的二阶展开：

$$
\exp(tX)\exp(sY) = \exp\left(tX+sY+\frac{st}{2}[X,Y] + o(s^2+t^2)\right).
$$

如果取$$s=t$$，则有

$$
\exp(tX)\exp(tY) = \exp\left(t(X+Y)+\frac{t^2}{2}[X,Y] + o(t^2)\right).
$$

此外，我们还有更一般的公式

$$
\exp(t_1X_1)\exp(t_2X_2)\cdots\exp(t_nX_n) = \exp\left(\sum_{i=1}^{n}t_iX_i + \frac{1}{2}\sum_{1\leqslant i<j\leqslant n}t_it_j[X_i,X_j] + o(\sum_{i=1}^{n}t_i^2)\right)
$$

这两个公式的证明相对于前两个公式而言，要困难许多。这里的证明参考的是王作勤老师的[笔记](http://staff.ustc.edu.cn/%7Ewangzuoq/Courses/13F-Lie/Notes/Lec%2008-09.pdf)。一般的李群的BCH公式的证明也可以在这篇笔记中找到。

---

对李群上的左不变向量场$$X\in\mathfrak{g}$$，它生成的$$G$$上的流为

$$
\Phi_t(g) = g\cdot \exp(tX)
$$

所以说

$$
\frac{\mathrm{d}}{\mathrm{d}t}\Big\vert_{t=0}f(g\cdot \exp(tX)) = \frac{\mathrm{d}}{\mathrm{d}t}\Big\vert_{t=0}f(\Phi_t(g)) = (Xf)(g)
$$

更进一步，对任意的$$t$$，有

$$
\begin{aligned}
    \frac{\mathrm{d}}{\mathrm{d}t}f(g\cdot \exp(tX)) &
    = \frac{\mathrm{d}}{\mathrm{d}s}\Big\vert_{s=0}f(g\cdot \exp((s+t)X)) \\
    & = \frac{\mathrm{d}}{\mathrm{d}s}\Big\vert_{s=0} f(g\cdot\exp(tX)\exp(sX)) \\
    & = (Xf)(g\cdot\exp(tX)) \\
\end{aligned}
$$

基于上式，由归纳法可以得到：对任意的$$k\geqslant 0$$，有

$$
\frac{\mathrm{d}^k}{\mathrm{d}t^k}f(g\cdot\exp(tX)) = (X^kf)(g\cdot\exp(tX))
$$

特别的，在$$t=0$$处有

$$
\frac{\mathrm{d}^k}{\mathrm{d}t^k}\Big\vert_{t=0}f(g\cdot\exp(tX)) = (X^{k}f)(g).
$$

上面的等式可以推广到多个向量场的情形。对两个左不变向量场$$X_1,X_2\in\mathfrak{g}$$以及$$k_1,k_2\geqslant 0$$，有

$$
\begin{aligned}
    \frac{\partial^{k_1+k_2}}{\partial t_1^{k_1}\partial t_2^{k_2}}\Big\vert_{(0,0)}f(g\cdot\exp(t_1X_1)\exp(t_2X_2))
    & = \frac{\mathrm{d}^{k_1}}{\mathrm{d}t_2^{k_1}}\Big\vert_{t_1=0}\left(\frac{\mathrm{d}^{k_2}}{\mathrm{d}t_2^{k_2}}\Big\vert_{t_2=0}f(g\cdot\exp(t_1X_1)\exp(t_2X_2))\right) \\
    & =\frac{\mathrm{d}^{k_1}}{\mathrm{d}t_1^{k_1}}\Big\vert_{t_1=0}(X_2^{k_2}f)(g\cdot\exp(t_1X_1)) \\
    & = (X_1^{k_1}X_2^{k_2}f)(g)
    \end{aligned}
$$

更一般地，有

$$
\frac{\partial^{k_1+\cdots+k_n}}{\partial t_1^{k_1}\cdots\partial t_n^{k_n}}\Big\vert_{(0,\dots,0)}f(g\cdot\exp(t_1X_1)\cdots\exp(t_nX_n)) = (X_1^{k_1}\cdots X_n^{k_n}f)(g)
$$

使用上面的等式就可以给出$$f(\exp(t_1X_1)\cdots\exp(t_mX_m))$$的泰勒展开：

> **结论**：对任意的光滑函数$$f \colon G \rightarrow \mathbb{R}^k$$，有
>
> $$
> f(\exp(t_1X_1)\cdots\exp(t_nX_n)) = \sum_{k_1+\cdots+k_n\leqslant N} \frac{t_1^{k_1}\cdots t_n^{k_n}}{k_1!\cdots k_n!}(X_1^{k_1}\cdots X_n^{k_n}f)(e) + O((t_1^{2}+\cdots+t_n^{2})^{\frac{N+1}{2}})
> $$

我们后面只关心二阶的展开：

$$
\begin{aligned}
    f(&\exp(t_1X_1)\cdots\exp(t_nX_n)) \\
    & = f(e)+ \sum_{i=1}^{n}t_i(X_if)(e) + \frac{1}{2}\sum_{i=1}^{n} t_i^2(X_i^2f)(e) + \sum_{1\leqslant i < j \leqslant n}t_it_j(X_iX_jf)(e) + O((t_1^2+\cdots+t_n^2)^{\frac{3}{2}}) \\
    & = f(e)+ \sum_{i=1}^{n}t_i(X_if)(e) + \frac{1}{2}\left((\sum_{i=1}^{n} t_iX_i)^2f\right)(e) + \frac{1}{2}\sum_{1\leqslant i < j \leqslant n}t_it_j([X_i,X_j]f)(e) + O((t_1^2+\cdots+t_n^2)^{\frac{3}{2}}) \\
\end{aligned}
$$

在上面的式子里，取$$f = \exp^{-1}\colon G\rightarrow \mathfrak{g}$$，可以算出，对任意的$$X\in\mathfrak{g}$$，有

$$
\begin{aligned}
    (X\exp^{-1})(e) & = \frac{\mathrm{d}}{\mathrm{d}t}\Big\vert_{t=0} \exp^{-1}(\exp(tX)) = \frac{\mathrm{d}}{\mathrm{d}t}\Big\vert_{t=0} tX = X, \\
    (X^{2}\exp^{-1})(e) & = \frac{\mathrm{d}^2}{\mathrm{d}t^2}\Big\vert_{t=0} \exp^{-1}(\exp(tX)) = \frac{\mathrm{d}^2}{\mathrm{d}t^2}\Big\vert_{t=0} tX = 0.
\end{aligned}
$$

所以上面的展开式会给出：

$$
\exp^{-1}(\exp(t_1X_1)\cdots\exp(t_nX_n)) = \sum_{i=1}^{n}t_iX_i + \frac{1}{2}\sum_{1\leqslant i < j \leqslant n} t_it_j [X_i,X_j] + O((t_1^2+\cdots+t_n^2)^{\frac{3}{2}}).
$$

也就是

$$
\exp(t_1X_1)\cdots\exp(t_nX_n) = \exp\left(\sum_{i=1}^{n}t_iX_i + \frac{1}{2}\sum_{1\leqslant i < j \leqslant n} t_it_j [X_i,X_j] + O((t_1^2+\cdots+t_n^2)^{\frac{3}{2}})\right).
$$

而这正是我们前面想要证明的公式。

---
layout: post
title: Bourgain's Trick: From Boundedness to Existence
date: 2025-07-11 23:02:33
description: This note records a trick in Bourgain's papers, which uses dual spaces and Hahn-Banach theorem to show existence of certain objects.
tags:
    
categories: Notes
toc:
    beginning: true
---

这篇笔记的目的是记录Bourgain在他的论文中使用的一个小技巧。这个技巧会导出这样的结果：一部分不等式会等价于特定对象的存在性。

这个技巧的关键是考虑适当空间$$\mathscr{X}$$的对偶空间$$\mathscr{X}^{*}$$，然后利用已知不等式和Hahn-Banach定理构造出$$\mathscr{X}^{*}$$中的元素。因为多数时候$$\mathscr{X}^{*}$$是某个已知的空间$$\tilde{\mathscr{X}}$$，所以我们会得到$$\tilde{\mathscr{X}}$$中特定元素的存在性。

这里给出两个例子，一个例子是散度方程$$\operatorname{div}F = u$$的解，这来自于Bourgain和Brezis合作的论文*New estimates for elliptic equations and Hodge type systems*，在网上也有[相关的内容](https://senyuyang-math.github.io/blog/2025/7.html)；另一个例子来自于Bourgain在论文*On Mahler's conjecture on the volume of a convex symmetric body and its polar*中不加证明地使用的结论。

## 散度方程的解

这一节里考虑的问题是，对给定的函数$$\rho\in L^{n}(\mathbb{R}^{n})$$，是否存在向量场$$F\in \left(L^{\infty}(\mathbb{R}^{n})\right)^{n}$$满足

$$
\operatorname{div}F = \rho.
$$

这一问题的回答是肯定的，我们直接给出证明。

首先我们有Sobolev不等式：

$$
\left\lVert u\right\rVert _{L^{\frac{n}{n-1}}} \leqslant C \left\lVert \nabla u\right\rVert _{L^{1}}, \quad \forall u \in C_{c}^{\infty}(\mathbb{R}^{n}).
$$

我们取$$\left(L^{1}(\mathbb{R}^{n})\right)^{n}$$的子空间

$$
S = \{\nabla u \mid u \in C_{c}^{\infty}(\mathbb{R}^{n})\}
$$

并考虑定义在$$S$$上的线性泛函

$$
\ell\colon \nabla u \longmapsto -\int_{\mathbb{R}^{n}}u\cdot \rho\,\mathrm{d}V
$$

注意因为$$u$$是紧支的，所以$$\nabla u\equiv 0$$会导出$$u\equiv 0$$，进而可以证明$$\ell$$是良定义的。又根据Sobolev不等式可以知道，$$\ell$$是有界的。因此根据Hahn-Banach定理，它可以延拓为$$\left(L^{1}(\mathbb{R}^{n})\right)^{n}$$上的有界线性泛函$$\mathcal{F}$$. 这时候有

$$
\mathcal{F}\in \left(\left(L^{1}(\mathbb{R}^{n})\right)^{n}\right)^{*} = \left(L^{\infty}(\mathbb{R}^{n})\right)^{n}
$$

我们设$$\mathcal{F}$$给出的$$\left(L^{\infty}(\mathbb{R}^{n})\right)^{n}$$中元素为$$F$$. 那么可以算出对任意的$$u\in C_{c}^{\infty}(\mathbb{R}^{n})$$有

$$
\int_{\mathbb{R}^{n}}u\cdot\operatorname{div}F\,\mathrm{d}V = -\int_{\mathbb{R}^{n}}F\cdot \nabla u\,\mathrm{d}V = -\mathcal{F}(u) = \int_{\mathbb{R}^{n}}u\cdot \rho\,\mathrm{d}V.
$$

这就说明$$\operatorname{div}F = \rho$$. 事实上，我们还能进一步给出$$\left\lVert F\right\rVert _{L^{\infty}}$$的估计：

$$
\left\lVert F\right\rVert _{L^{\infty}} \leqslant C\cdot \left\lVert \rho\right\rVert _{L^{n}}
$$

## 特定测度的存在性

我们展示这样一个结果

> **定理**：我们假定Bernstein不等式成立，即存在常数$$C>0$$，使得对任意的$$d$$次多项式$$p(t),t\in [-1,1]$$，有不等式
>
> $$
> \left\lvert p'(0)\right\rvert \leqslant C\cdot d \cdot \sup_{[-1,1]}\left\lvert p(t)\right\rvert
> $$
>
> 那么对每个$$d\geqslant 1$$，存在一个$$[-1,1]$$上的Borel测度$$\nu$$满足
>
> $$
> \begin{cases}
> \left\lVert \nu\right\rVert \leqslant C \cdot d, \\
> \int_{[-1,1]}t\,\mathrm{d}\nu(t) = 1, \\
> \int_{[-1,1]}t^{k}\,\mathrm{d}\nu(t) = 0, \forall 1 < k \leqslant d.\\
> \end{cases}
> $$
>
我们的办法是类似的：考虑函数空间$$C([-1,1])$$（其上范数为$$L^{\infty}$$-范数）的子空间

$$
S = \{p(t) = \sum_{k=0}^{d}a_{k}t^{k} \mid a_{k} \in \mathbb{R}\}
$$

在其上可以定义线性泛函

$$
\ell\colon p(t) \longmapsto p'(0)
$$

Bernstein不等式告诉我们，$$\ell$$是有界的，因此可以延拓为$$C([-1,1])$$上线性泛函$$\mathscr{L}$$，使得$$\left\lVert \mathscr{L}\right\rVert \leqslant C\cdot d$$. 注意到有

$$
\bigl(C([-1,1])\bigr)^{*} = \{[-1,1]\text{上Borel测度}\}
$$

因此我们可设$$\mathscr{L}$$给出的Borel测度为$$\nu$$. 则有$$\left\lVert \nu\right\rVert \leqslant C\cdot d$$，且

$$
\begin{aligned}
 \int_{[-1,1]}t\,\mathrm{d}\nu(t) & = \mathscr{L}(t) = 1, \\
 \int_{[-1,1]}t^{k}\,\mathrm{d}\nu(t) & = \mathscr{L}(t^{k}) = 0. \\
\end{aligned}
$$

这就完成了证明。

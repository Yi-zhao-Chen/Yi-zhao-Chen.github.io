---
layout: post
title: An Application of the Uniform Boundedness Principle - On the Continuity of Lie Group's Representations(In Chinese)
date: 2025-09-19 20:44:12
description: Provide an application of the uniform boundedness principle that is not so "analytic".
tags:
  
categories: Notes
---

所谓的共鸣定理是指

> **定理**(共鸣定理/一致有界定理)：对Banach空间$$X,Y$$之间的一些有界线性映射$$W\subseteq \mathscr{L}(X,Y)$$（这里$$\mathscr{L}(X,Y)$$表示$$X$$到$$Y$$的全体有界线性映射构成的集合），如果对任意的$$x\in X$$都有
>
> $$
> \sup_{A\in W} \Vert Ax\Vert < +\infty
> $$
>
> 那么$$W$$是$$\mathscr{L}(X,Y)$$中的有界集，即存在$$M>0$$使得
>
> $$
> \sup_{A\in W} \Vert A \Vert_{op} \leqslant M
> $$

在我阅读的泛函分析的教材中，共鸣定理（或一致有界定理）的应用基本都和分析有关。这篇笔记中，我们给出一个稍微不那么“分析”的例子：我们展示如何使用共鸣定理提升李群在Banach空间上的表示的连续性。

我们先给出李群在Banach空间上的表示的定义。

> **定义**：对李群$$G$$，它在一个实或复Banach空间$$X$$上的表示是一个群同态
>
> $$
> \pi \colon G \longrightarrow \operatorname{GL}(X)
> $$
>
> 其中$$\operatorname{GL}(X)$$是$$X$$上全体线性同胚构成的集合。此外要求$$\pi$$是强连续的，即对任意的$$x\in X$$，从$$G$$到$$X$$的映射
>
> $$
> G \ni g \longmapsto \pi(g)x \in X
> $$
>
> 是连续的。

在$$X$$是有限维向量空间时，$$X$$拥有一个标准的拓扑，在这个拓扑下任何线性映射都是连续的，这时候上面的定义正好给出李群的有限维表示。

> **注记**：在其他材料中可能会用其他的词语来称呼这里的“强连续”。我们这里借用了泛函分析中强连续半群中的术语。事实上，强连续是使得$$G$$的李代数能够被表示为$$X$$上算子所需要的最低要求。

对李群在拓扑空间上的作用，我们还有一种定义连续性的办法：注意到李群$$G$$在$$X$$上的表示也给出了它在拓扑空间$$X$$上的作用，进而有拓扑空间之间的映射

$$
G \times X \longrightarrow X
$$

如果这一映射是连续的，我们就称李群$$G$$的表示是连续的。不难看出，和字面意思相反，“强连续”实际上比“连续”要弱。

我们接下来要说明的是，实际上强连续和连续是等价的，也就是：

> **命题**：对李群$$G$$在Banach空间$$X$$上的表示$$\pi$$，它诱导的映射
>
> $$
> \begin{aligned}
> G \times X & \longrightarrow X \\
> (g,x)& \longmapsto \pi(g)x
> \end{aligned}
> $$
>
> 是连续的。

我们任取一列$$(g_{n},x_{n})\in G\times X$$满足

$$
(g_{n},x_{n}) \to (g,x) \in G\times X
$$

因为$$g_{n} \to g$$，所以可以假设$$\{g_{n}\}$$落在$$G$$的一个紧子集$$K$$内。考虑$$\mathscr{L}(X,X)$$的子集

$$
\pi(K) = \{\pi(h) \mid h\in K\}
$$

对任意的$$x\in X$$，强连续性告诉我们，映射

$$
\begin{aligned}
 G & \longrightarrow X \\
 h & \longmapsto \pi(h)x \\
\end{aligned}
$$

是连续的，所以紧集$$K$$被映为$$X$$中紧集$$\{\pi(h)x \mid h\in K\}$$，特别的，它也是$$X$$中有界集。所以使用共鸣定理可以知道，$$\pi(K)$$是$$\mathscr{L}(X,X)$$中的有界集。我们设

$$
\Vert \pi(h) \Vert_{op} \leqslant M,\quad \forall h\in G
$$

进而有：

$$
\begin{aligned}
 \left\lVert \pi(g_{n})x_{n} - \pi(g)x\right\rVert & = \left\lVert \pi(g_{n})(x_{n}-x) + \pi(g_{n})x - \pi(g)x \right\rVert \\
 & \leqslant \left\lVert \pi(g_{n})\right\rVert _{op}\cdot\left\lVert x_{n}-x\right\rVert + \left\lVert \pi(g_{n})x-\pi(g)x\right\rVert \\
 & \leqslant M \left\lVert x_{n}-x\right\rVert + \left\lVert \pi(g_{n})x-\pi(g)x\right\rVert \\
\end{aligned}
$$

根据$$x_{n} \to x$$和$$\pi$$强连续可以得到，上面不等式右侧趋于$$0$$，因此左侧也趋于$$0$$，也就是$$\pi(g_{n})x_{n}\to \pi(g)x$$. 这和$$(g_{n},x_{n})$$任意性结合就得到了$$\pi$$的连续性。

> **注记**：实际上可以将定理中的“李群”的要求减弱为“局部紧致的拓扑群”。

---

事实上，我们无法将强连续进一步提高为映射$$\pi$$的连续性。在这个意义上，我们得到的结果是最优的。比如考虑$$\mathbb{R}$$在平方可积函数空间$$L^{2}(\mathbb{R})$$上的平移作用

$$
\left(\pi(h)f\right)(x):= f(x+h)
$$

可以验证它是强连续的（事实上它是算子$$\frac{\mathrm{d}}{\mathrm{d}x}$$生成的强连续单参数酉群），但对任意的$$h>0$$，如果取

$$
f_{h}(x) =
\begin{cases}
 1, & 0\leqslant x \leqslant h;\\
 0, & \text{otherwise}.
\end{cases}
$$

那么可以算出

$$
\left\lVert \pi(h)-\pi(0)\right\rVert _{op}\geqslant \frac{\left\lVert \pi(h)f_{h}-f_{h}\right\rVert}{\left\lVert f_{h}\right\rVert} = \sqrt{2}
$$

这说明$$\pi$$不可能是连续的。

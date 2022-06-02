---
title: 'Eikonal Equation and SDF'
date: 2022-06-01
permalink: /posts/2022/06/eikonal/
excerpt: ""
tags:
  - mathematics
---

在NeuS[1]中使用了eikonal loss, 即$$(|\nabla\mathcal{f}(\mathbf{p})|-1)^2=0$$, 该损失的加入是为了约束MLP满足SDF的性质, 那为什么Signed Distance Function(SDF)的导数模长为1呢?

下面给出一个简单证明

假设$$\mathcal{f}(\mathbf{p})$$是定义在$$\Omega$$上的SDF, $$\Omega$$属于$$\mathbb{R}^n$$上的开子集, 对点$$\mathbf{x}\notin\partial\Omega$$存在一个最近点$$y\in\partial\Omega$$, 因此$$\mathbf{y}-\mathbf{x}$$是最速下降方向即与$$\nabla\mathcal{f}(\mathbf{x})$$同方向, 同时由于$$\mathcal{f}$$恰好表示到最近点的距离,
因此沿$$\mathbf{y}-\mathbf{x}$$方向移动一单位$$\mathcal{f}$$也变化一单位, 即$$D_v\mathcal{f}=\nabla\mathcal{f}(\mathbf{x})\cdot v=1, v=\frac{\mathbf{y}-\mathbf{x}}{\norm{}{\norm{x}}$$}}$$
故|grad_f(x)|=1

Eikonal equation (程函方程) 
<center>$$ |\nabla u(x)|=n(x) $$</center>
其中$$x$$属于$$\mathbb{R}^n$$上的开子集, $$n(x)>0$$


fast marching method (FMM) to solve eikonal equation, a special case of dijkstra algorithm
wave propagation
maxwell's equation
signed distance function

implicit surface


[1] 
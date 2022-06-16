---
title: 'Eikonal Equation and SDF'
date: 2022-06-01
permalink: /posts/2022/06/eikonal/
excerpt: ""
tags:
  - mathematics
---

### SDF的导数性质
<br>
在NeuS[1]中使用了eikonal loss, 即$$(\lVert\nabla\mathcal{f}(\mathbf{p})\rVert-1)^2=0$$, 该损失的加入是为了约束MLP满足SDF的性质, 那么为什么Signed Distance Function(SDF)的导数模长为1呢?

下面给出一个简单证明

假设$$\mathcal{f}(\mathbf{p})$$是定义在$$\Omega$$上的SDF, $$\Omega$$属于$$\mathbb{R}^n$$上的开子集, 对点$$x\notin\partial\Omega$$存在一个最近点$$y\in\partial\Omega$$, 因此$$v=\frac{y-x}{\lVert y-x \rVert}$$是最速下降方向即与$$\nabla\mathcal{f}(\mathbf{x})$$同方向

又因$$\mathcal{f}$$恰好表示到最近点的距离, 故沿$$v$$方向移动一单位$$\mathcal{f}$$也变化一单位, 即方向导数满足$$D_v\mathcal{f}=\nabla\mathcal{f}(\mathbf{x})\cdot v=\lVert\nabla\mathcal{f}(x)\rVert \lVert v \rVert \cos(\theta)=1$$

故$$\lVert\nabla\mathcal{f}(x)\rVert=1$$

### Eikonal equation (程函方程)
<center>$$ |\nabla u(x)|=n(x) $$</center>

其中$$x$$属于$$\mathbb{R}^n$$上的开子集, $$n(x)>0$$

Helmholtz Equation
$$\nabla^2f=-k^2f$$


波动方程由麦克斯韦方程组导出, 亥姆霍兹方程来自于可分离变量的波动方程, 程函方程则来自于亥姆霍兹方程的一般解, 程函方程的具体导出可以参考诺贝尔奖得主Max Born的经典著作***光学原理-光的传播, 干涉和衍射的电磁理论***

程函方程揭示了波在空间中传播时形状的轨迹(trace of the shape), 也是几何光学(geometric optics)中对波动方程的本质近似(fundamental approximation)  

几何光学中对光使用光线(ray)进行建模, 也是图形学渲染中着色理论使用的基本模型

而求解程函方程的fast marching method(FMM)则是最短路径算法(Dijkstra)的一个特例

你看, 物理学和计算机如此美妙的结合在了一起

[1] NeuS: Learning Neural Implicit Surfaces  by Volume Rendering for Multi-view Reconstruction
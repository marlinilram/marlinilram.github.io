---
title: "A Simple Interactive Registration Method for 3D Volumetric Medical Image"
collection: publications
permalink: /publication/2017-cranio
excerpt: 'We propose an interactive registration technique based on an efficient deformation algorithm.'
date: 2017-02-09
venue: 'Journal of Computer-Aided Design & Computer Graphics 计算机辅助设计与图形学学报'
---

Lin Ma, Hui Huang 
[project page](http://vcc.szu.edu.cn/research/2017/SAFIntReg.html)/[code](https://github.com/marlinilram/cranioviewer)  

<p style="text-align:center;">
	<img src="/images/20170330162547_416.jpeg" alt=""> 
</p>
<p style="text-align:center;">
	<strong>图</strong><strong>1</strong> 3 组非刚性配准结果
</p>
<p style="text-align:center;">
	<br>
</p>
<p>
	<span style="color:#000000;font-size:16px;"><strong>摘 要</strong></span> 
</p>
<p>
	&nbsp; &nbsp; &nbsp; 对高分辨率体数据构成的医学图像进行隐式曲面配准是一件耗时的工作, 对于发育未完全的儿童头骨中包含的大量不连续空洞这样的复杂情况, 全自动算法一般难以处理, 为此提出一种交互式的快速配准方法. 首先对一定范围内体数据进行采样得到目标点集; 而后将定义在模板网格上的局部最刚性变换能量引入非刚性最近点迭代配准中作为自动配准框架; 在此基础上, 加入用户实时交互对局部区域结果进行调整与优化. 实验结果表明, 对于平均120 万体素采样点, 该方法能够在13 s 内完成配准过程, 并且与marching cubes 结果具有相似准确度.
</p>
<p>
	<br>
</p>
<p>
	<span style="color:#000000;font-size:16px;"><strong>Abstract</strong></span> 
</p>
<p style="text-align:justify;">
	It is time consuming for surface registration of medical volumetric images in high resolution. Fully automatic methods cannot handle complex situations well, for example, massive non-continuous holes in children’s skull. To address this problem, we propose an interactive registration technique based on an efficient deformation algorithm. We first sample the volumetric data; combine local as-rigid-as-possible energy with non-rigid iterative closest point as an automatic registration framework and integrate real-time interactive refinement in local regions. The experiments demonstrate our technique is able to complete the registration in 13 seconds for an average 1.2 million sample points with the same accuracy by marching cubes.
</p>
<p>
	<br>
</p>
<p style="text-align:center;">
	<img src="/images/20170330162746_133.jpeg" alt=""> 
</p>
<p style="text-align:center;">
	<strong>图</strong><strong>2</strong> 系统流程图
</p>
<p style="text-align:center;">
	<br>
</p>
<p style="text-align:center;">
	<img src="../../viewFile/0/58/attached/image/20170330/20170330162918_1.jpg" width="500" height="278" alt=""> 
</p>
<p style="text-align:center;">
	<strong>图3</strong> iso 曲面实例
</p>
<p>
	<br>
</p>
<p>
	<span style="font-size:16px;color:#000000;"><strong>结 语</strong></span><br>
&nbsp; &nbsp; &nbsp; 本文结合图形学里的快速变形算法, 提出了一种新的医学图像曲面快速配准算法, 并且加入了用户的交互, 从而实现了对配准过程进行局部优化. 实验结果表明, 本文方法最终生成的配准模型与MC 算法提取的iso 曲面十分接近, 并且能够通过使用同一模板对不同CT 数据配准获得不同CT 图像之间的对应关系, 实现如morphing 等更高级的应用; 当对足够的CT 图像进行配准后, 可以得到对该疾病各种不同类型头骨畸形形状的数据库, 同时这些配准后的头骨模型具有完全相同的网格拓扑结构, 利用统计学习的方法可以对症状进行分类, 以及更精确的畸形程度度量等. 除此之外, 本文也认为, 交互式配准工具是对现有配准工具的有利补充, 由于医学数据的复杂性, 全自动算法必然存在一些无法良好处理的特例. 在将来的工作中可以继续改进配准中的交互功能, 例如, 利用学习到的统计模型预测配准不准确的部位, 启发式地提示用户在该部分进行局部改善.
</p>

<p style="font-family:GothamRnd-Light, " font-size:12px;background-color:#ffffff;text-align:justify;"=""> <span style="font-size:18px;"><span style="font-size:14px;"><strong><span style="font-size:18px;">Bibtex</span></strong><br>
<span style="font-size:12px;">@article{SAFIntReg17,&nbsp;</span><br>
<span style="font-size:12px;">title&nbsp;=&nbsp;{</span></span><span style="font-size:12px;">A Simple Interactive Registration Method for 3D Volumetric Medical Image</span><span style="font-size:14px;"><span style="font-size:12px;">},</span><br>
<span style="font-size:12px;">author&nbsp;=&nbsp;{Ma Lin and Hui Huang},</span><br>
<span style="font-size:12px;">volume&nbsp;=&nbsp;{29},</span><br>
</span></span> 
	</p>
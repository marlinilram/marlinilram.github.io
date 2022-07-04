---
title: '[PaperReading] Neural 3D Reconstruction in the Wild, SIGGRAPH 2022'
date: 2022-05-31
permalink: /posts/2022/05/neural-recon-wild/
excerpt: ""
tags:
  - 3d reconstruction
  - nerf
---

[project](https://zju3dv.github.io/neuralrecon-w/)

---

## Contribution

a new method that enables efficient and accurate surface reconstruction from Internet photo collections in the presence of varying illumination

1. a hybrid voxel- and surface- guided sampling technique that allows for more efficient ray sampling around surfaces and leads to significant improvements in reconstruction quality
2. a new benchmark and protocol for evaluating reconstruction performance on such in-thewild scenes

---

## Motivation

两个task setup 
1. mesh output instead of radiance field, 因此借助了NeuS[1]的思想
2. internet images in the wild, 数量大NeuS太慢, 需要更快的采样方式

---

## Approach

0. 针对unconstrained 网络图像, 借鉴NeRF-W思路增加latent appearance code
1. voxel-guided 
   - 利用sfm的稀疏点云初始化稀疏voxel grid, 并且额外进行3D膨胀保证surface被容纳
   - 与instant-ngp[2]类似通过维护一个稀疏voxel grid在采样过程中快速跳过void space
   - 采样光线数可以减少30%
2. surface-guided
   - 由于是SDF表示, 在训练过程中缓存sdf值到voxel grid中记录surface位置, 在surface附近(x-t_s, x+t_s)增加采样点, sdf值定期更新
   - This strategy guides the network to explain the rendered color with near-surface samples, leading to more accurate geometric fitting
3. transient object
   - NeRF-W使用transient head来建模动态物体, 容易dominate颜色, 导致geometry的变化被解释成view-dependent效果
   - 使用segmentation mask来避免使用属于动态物体的光线
4. loss and sky
   - loss_color, loss_reg, loss_mask, 参考NeuS[1]

---

[1] NeuS: Learning Neural Implicit Surfaces by Volume Rendering for Multi-view Reconstruction  
[2] Instant Neural Graphics Primitives with a Multiresolution Hash Encoding
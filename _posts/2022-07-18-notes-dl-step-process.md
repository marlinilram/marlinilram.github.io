---
title: '[Notes] Step-by-step process to set up deep learning projects -- Matthias Niessner'
date: 2022-06-17
permalink: /posts/2022/06/taichi-nerf/
excerpt: ""
tags:
  - taichi
  - nerf
---

General advice: start simple -> use a small architecture (less than 1 mio params). In vision, ENet or a crippled ResNet-18 (only the first blocks) is a good choice. Common mistake: train model with 100mio+ params for 3 weeks only to notice that the data loader is broken.  
从简单模型开始(参数量小于1百万)

No fancy features: disable dropout, no batchnorm, no learning rate decay, etc. These may give you a few % points at the end, but at the beginning they complicate everything; e.g., LR decay often falsely makes train curves look like they are converged.  
关闭非必要的训练trick, 例如dropout, batchnorm, lr decay等等, lr decay常常错误地让训练曲线看起来收敛

Set up train/val: loss curves are all you have for debugging (TensorBoard is a great tool). Make sure to log loss for every batch (not just once an epoch); log val the same way as train: i.e., after every iteration run a forward pass for a random batch from the val set.  
观察loss曲线, 记录每一个batch的loss信息(包括所有的epoch), 对val数据也要记录同样的loss信息, 每一个迭代后对测试集的一组随机batch进行一次前向推理

Overfit to a single train sample first: this debugs your output, which you expect the network to fully memorize. If you turn off all regularizes, such as weight decay, train loss should go to zero. Note that the input to the network will be ignored in this experiment.  
对单个数据进行过拟合测试: 对输出进行调试确保网络对该情况进行了完全记忆, 在关闭了所有的正则时, 训练loss应该为0

Overfit to 5-10 train samples: now the network needs to predict different outputs depending on the input. For tasks like classification, train loss should still go to zero and training should take at most a few minutes. Val loss will go up as you don’t learn anything yet.  
对5-10个数据进行过拟合测试

With the previous steps, you verified data loading and whether basic optimizing works. Now it’s time to throw more data at the problem. Here, the goal is generalize for the first time – if your val loss goes down (even just slightly), congrats, you learned something :)  
基本的优化框架验证有效后开始加入更多的数据, 关注泛化能力

Training speed: given that deep learning is so empirical, it’s critical that your setup facilitates fast turnaround times for debugging. Make sure you understand where the bottle neck lies (data loading vs backprop); a single batch should be processed in under a second.  
尽早准备好方便重复调试的辅助工具, 明确性能瓶颈(数据加载 vs 梯度回传), 一个batch应该在1s内完成

Once you have the basic setup running, it’s finally time to improve the overall performance. In addition to the train/val curves, you want to log curves for metrics, such as mIoU, accuracy, F1, etc., on the val set; visualize these during training.  
记录更多的指标信息, 并在训练过程中可视化

Run many ablations at the same time: already after a few iterations / few minutes of training, loss curves and metrics tell you whether an experiment has promise or not. Kill experiments that don’t show promise and start new ones with different hyper parameters.  
同时进行多个消融实验, 在若干训练迭代/时间后即可观察出该组超参数大致效果, 即时停止旧实验, 尝试新的参数

Data engineering: mostly, your performance is limited due to data (e.g., overfitting). Here, weight balancing between classes and augmentations (e.g., rotations, noise, etc.) come into play. Important: never augment the val set as it would make it impossible to compare.   
大多时候性能受限于数据, 此时需要考虑数据分布类别均衡性以及数据增强

For generative models, such as GANs, always start without a discriminator loss. Instead, just do a simple L1 regression first - only once that works, add the D (Wasserstein is a good choice). GANs mostly struggle due to data issues -> start with a simple distribution.  
对于生成式模型, 从L1正则同时关闭判别器loss开始, 在L1有效后, 再加上D. GANs对数据敏感, 从一个简单分布开始

Finally, it’s time to try out bigger architectures. ResNet-XXX, InceptionNet, XceptionNet etc. are good choices, and try out other features which we removed before (dropout, batchnorm, LR decay, etc.). If you have the compute resources, make sure multi-GPU training works.  
上述步骤都验证之后, 开始尝试大模型, tricks以及多GPU训练

Final advice when using methods from research papers in AI/ML: be aware that all papers are written to sell a specific point -> they are rarely proposing an easy-to-implement method. Often, it’s much better to use the simple baseline that many SOTA papers claim to beat.  
对于使用research paper, 从他们声称超越的baseline方法开始常常是更好的选择

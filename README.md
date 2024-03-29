# mechine-Learning
关于机器学习的笔记 

---
layout: post
title: Github 博客画流程图
category: how2blog
tags: [tools, study, markdown]
mermaid: true
---

# 1.1基本概念
**信息熵**：$Ent(D) = -\sum_{k=1}^{|\gamma|}p_k\log_2p_k$ ，
$Ent(D)$的值越小，则$D$的纯度越高。

**信息增益**：
$$Gain(D,a) = Ent(D) - \sum_{v=1}^{V}\frac{|D^v|}{|D|}Ent(D^v)$$
信息增益越大， 意味这使用属性$a$来进行划分所获得的“纯度提升”越大。

选择属性时，考虑的是信息增益最大者， 即$a_* = \underset{a\in\mathrm{A}}{\arg\min}\ Gain(D,a)$

**增益率**：实际上，信息增益准则对可能取值数目较多的属性有所偏好，为减少这种偏好可能带来的不利影响，引入了“增益率”的定义
$$Gain\underline{\hspace{0.5em}}ratio(D,a) = \frac{Gain(D,a)}{IV(a)}$$
其中$$IV(a) = -\sum_{v=1}^{V}\frac{|D^v|}{|D|}\log_2\frac{|D^v|}{|D|}$$
选择属性时，先从候选划分属性中找出信息增益高于平均水平的属性，再从其中选择增益率最高的。

**基尼指数**：CART决策树使用“基尼指数”来选择划分属性。数据集$D$的纯度可由基尼值来度量：
$$Gini(D) = \sum_{k=1}^{|\gamma|}\sum_{k'\neq k}p_kp_{k'}$$
直观来说，$Gini(D)$反应了从数据集$D$中随机抽取两个样本，其类别标记不一致的概率。因此，$Gini(D)$越小，则数据集$D$的纯度越高。

属性$a$的基尼指数定义为$$Gini\underline{\hspace{0.5em}}index(D,a) = \sum_{v=1}^{V}\frac{|D^v|}{|D|}Gini(D^v)$$
于是，再候选属性集合$A$中，选择那个使得使得划分后基尼指数最小的属性作为最优划分属性，即
$a_* = \underset{a\in\mathrm{A}}{\arg\min}\ Gini\underline{\hspace{0.5em}}index(D,a)$。

## 1.2决策树
```
graph TD
    A[纹理=?] -->|清晰|B[根蒂=?]
    A -->|稍糊|C[触感=?]
    A -->|模糊|D[坏瓜]
    B -->|蜷缩|B1[好瓜]
    B -->|稍蜷|B2[色泽=?]
    B -->|硬挺|B3[坏瓜]
    C -->|硬滑| E[坏瓜]
    C -->|软黏| F[好瓜]
    B2 -->|青绿| B21[好瓜]
    B2 -->|乌黑| B22[触感=?]
    B2 -->|浅白| B23[好瓜]
    B22 -->|硬滑| B221[好瓜]
    B22 -->|软黏| B222[坏瓜]
    
```



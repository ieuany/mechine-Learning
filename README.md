# mechine-Learning
关于机器学习的笔记 

# 1.1决策树是什么
**信息熵**：$Ent(D) = -\sum_{k=1}^{|\gamma|}p_k\log_2p_k$
$Ent(D)$的值越小，则$D$的纯度越高。

**信息增益**：
$$Gain(D,a) = Ent(D) - \sum_{v=1}^{V}\frac{|D^v|}{|D|}Ent(D^v)$$
信息增益越大， 意味这使用属性$a$来进行划分所获得的“纯度提升”越大。

选择属性时，考虑的是信息增益最大者， 即$a_* = \mathop{\arg\min}_{a\in\mathrm{A}}Gain(D,a)$

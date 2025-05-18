


# 冠状动脉模型

参考文献:

1. {cite:p}`barnafi2022multiscale`
2. {cite:p}`richardson2024cardiac`
3. 钟倩
4. 端木正


## 0D 冠状动脉模型
我们主要使用 **钟倩**,  **端木正** 和 {cite:p}`barnafi2022multiscale`的工作都是基于0D模型的。

###  {cite:p}`barnafi2022multiscale`
我主要看了 {cite:p}`barnafi2022multiscale` 这篇文章。

#### 主要的概念
每一段血管分为近端(proxmal)和远端(distal), 它的状态由四个物理量 $P_d$, $P_p$, $Q_d$, $Q_p$ 描述。
而常微分方程中的 $Q$ 和 $P$ 分别是近端和远端的线性插值，
$$
Q=\beta Q_p + (1-\beta) Q_d
Q=\alpha Q_p + (1-\alpha) Q_d
$$



#### 参数取值
这里的 $\alpha$ $\beta$ 可以取成一样的，计作 $\chi$, 可以取$0,0.5,1.0$。取成0.5比较好。

#### 初始条件

#### 边界条件



## 冠状动脉模型与心肌灌注模型的耦合

单向耦合。心脏的主动收缩力不受心肌灌注的影响，只对冠状动脉的末端流量和心肌的灌注压强两者进行耦合。具体来说，
是显式求解，冠状动脉给心肌流量，心肌给冠状动脉压强。




````{note} 单向耦合。
/Users/pengfei/GitHub/tutorial/doc/source/4-cardiac-perfusion/coronary.md:25: ERROR: Content block expected for the "note" directive; none found.
````

$$
e=mc^2
$$
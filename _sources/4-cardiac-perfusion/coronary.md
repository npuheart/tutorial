


# 冠状动脉模型

epicardial coronary vessels

参考文献:

1. 文献一: {cite:p}`barnafi2022multiscale`
2. {cite:p}`richardson2024cardiac`
3. {cite:p}`zhong2022master`
4. 端木正


## 0D 冠状动脉模型
我们主要参考了 **钟倩**,  **端木正** 和 {cite:p}`barnafi2022multiscale`的工作, 这些研究均基于0D模型的.

### 模型一

> {cite:p}`barnafi2022multiscale` 

#### 主要的概念
物理参数
: 每段血管由以下**物理参数**表征：
- 几何参数：长度 $\ell$, 横截面积 $A$, 壁厚 $H$
- 流体性质：密度 $\rho_f$, 粘度 $\mu_f$
- 管壁力学：杨氏模量 $E$, 泊松比 $\nu$

控制方程
: (质量守恒与动量守恒方程)为：

$$
\begin{aligned}\tag{1-1}
L \frac{d Q}{d t} + R Q + P_d - P_p &= 0 \quad &\text{(动量方程)} \\
C \frac{d P}{d t} + Q_d - Q_p &= 0 \quad &\text{(质量方程)} \\
Q(0) &= Q_0 \quad &\text{(初始流量)} \\
P(0) &= P_0 \quad &\text{(初始压力)}
\end{aligned}
$$ (mymath2)


{eq}`mymath2`中的参数为, 


$$
\begin{cases}
R = \dfrac{K_r \ell}{A^2} & \text{流动阻力} \\
L = \dfrac{\rho_f \ell}{A} & \text{流体惯性} \\
C = \dfrac{A^{3/2} \ell}{\eta} & \text{血管顺应性} \\
K_r = 8\pi\mu_f & \text{粘性阻力系数} \\
\eta = \dfrac{\sqrt{\pi} H E}{1-\nu^2} & \text{管壁刚度系数}
\end{cases}
$$

$Q$为体积流量(volumetric flow rate), $P$为平均压力(mean pressure), 是待求解的物理量。但是，
我们并不直接使用$P$和$Q$.  其状态由四个物理量描述： 
- $P_d$: 远端压力 
- $P_p$: 近端压力 
- $Q_d$: 远端流量
- $Q_p$: 近端流量

$P$和$Q$分别为近端和远端的线性插值：

$$
\begin{aligned}
Q &= \beta Q_p + (1-\beta) Q_d \\
P &= \alpha P_p + (1-\alpha) P_d 
\end{aligned}
$$

因此，每个血管段都要求解四个未知量。

![image-20250518210255252](https://githubimages.pengfeima.cn/images/202505182102409.png)
节点记为$n$, 每段血管分为近端（proximal）和远端（distal）两个端点, 节点的集合为$\mathcal{N}$, 
每个血管段记为$S=\{n_p, n_d\}$, 
血管段的集合为$\mathcal{S}$. 其中有特殊情况, 
入口出口处的血管段$S^i$仅含出口节点 $S^o$ 仅含入口节点.



#### 参数取值
文中建议保持$\alpha=\beta=\chi$, 典型取值$\chi=0.5$。
这里的 $\alpha$ $\beta$ 可以取成一样的, 计作 $\chi$, 可以取$0, 0.5, 1.0$.取成0.5比较好.

#### 初始条件

#### 边界条件

1. 血管在每个节点处，满足以下边界条件：

$$
\sum_{i \in \mathcal{S}_n^i} Q_d^i=\sum_{j \in \mathcal{S}_n^o} Q_p^j \quad \forall n \in \mathcal{N}, \quad P_d^i=P_p^j \quad \forall i \in \mathcal{S}_n^i, j \in \mathcal{S}_n^o
$$

2. 在冠状动脉的入口处满足：

$$
P_p^s=p_{\text {ao }} \quad \forall s \in \mathcal{S}^{\text {in }}
$$

3. 冠状动脉的出口处满足：

$$
P_d^o=\frac{1}{\left|\Omega_o\right|} \int_{\Omega_o} p_1 d X \quad \forall o \in \mathcal{S}^{\text {out }}
$$


```{note}
单向耦合.心脏的主动收缩力不受心肌灌注的影响, 只对冠状动脉的末端流量和心肌的灌注压强两者进行耦合.具体来说, 
是显式求解, 冠状动脉给心肌流量, 心肌给冠状动脉压强.
```



### 模型二


1. 冠状动脉的每个出口都有终端阻抗 $Z$
2. 根据入口压强、出口压强和终端阻抗计算出终端流量
3. 计算出剩下的物理量


## 1D 冠状动脉模型
（内容待补充）







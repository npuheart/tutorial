
# 耦合的耦合

冠状动脉模型与多孔弹性模型的耦合

## 模型一

> {cite:p}`barnafi2022multiscale` 还没完全看明白



1. 主动脉压强 $p_{\text {ao }}$ 从windkessel模型获取
2. 心肌压强 $p_1$ 从心肌灌注模型获取
3. 出口流量 $Q^o$ 反馈给心肌灌注模型

$$
\left.\theta_1\right|_{\Omega_o}=\frac{1}{\left|\Omega_o\right|} Q^o=\frac{\alpha^o Q_d^o+\left(1-\alpha^o\right) Q_p^o}{\left|\Omega_o\right|} \quad \forall o \in \mathcal{S}^{\text {out }}
$$

```{note}
$\theta_1$ 为从冠状动脉流入心肌的血液，要减去从静脉流走的血液。
```


$$
\theta_{NC} =  - \underbrace{\gamma (p_{\text{NC}} - p_{\text{veins}})}_{\text{静脉回流}}
$$



其中：
- $\gamma = 10^{-4}$ 为静脉回流系数（单位：mL/(s·Pa)）
- $p_{\text{veins}} = 1\,\text{kPa}$ 为静脉基准压力
- $NC=2$, $p_{\text{NC}}$ 分别为 $p_1=p_\text{art}$ $p_2=p_\text{cap}$ (这里我不太清楚，得问问作者)

**物理意义**：
需要计算心肌净血液供应量，由冠状动脉灌注量减去静脉回流量构成，其中静脉回流量服从Starling定律，与心肌-静脉压力差成正比。(Starling 定律的参考文献呢？)


## 模型二

> {cite:p}`{see}chapelle2010poroelastic{section 4.3}` . See also {cite:p}`richardson2021poroelastic`.

根据血液流向，心脏中的血管可分为
冠状动脉(coronary arteries)、小动脉(arterioles)、毛细血管(capillaries)、小静脉(venules)和静脉(veins)，
心肌灌注模型中的压强描述的是毛细血管中的压强。

```{note}
Chapelle et al. 提出的 single compartment poroviscoelastic model 意思是所有灌注区域都是连通的。
分区域灌注就是 multi-compartment.
```

$$
s=\beta_a\left(p_a-p\right)-\beta_v\left(p-p_v\right)
$$

$p_a$ 和 $p_v$ 分别是小动脉和小静脉的压强。


## 模型三
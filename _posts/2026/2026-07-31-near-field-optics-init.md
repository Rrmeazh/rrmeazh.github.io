---
title: "近场光学初探"
date: 2026-07-31 00:00:00 +0800
categories: [Courses, Physics]
tags: [Optics]
math: true

description: 记录24年做SRT项目整理的若干知识
---

> **PREFACE**  
>
> 这是本人本科阶段唯一一段，可能也是这辈子最后一段物批经历了。高考后的暑假里，本人在短短几天内先是被意向院校顺利录取，而后又突然被发配到土水方向。蒙此大起大落，再加上彼时完全没有放开转专业，本人一度心志沉沦。或许是出于一种对高中三年物批时光带着滤镜的追忆，本人在24年春报名了物理系老师立项的SRT——近场光学。虽然到了后期师生都开摆了，并没有做多少工作，但对于彼时的本人，这个项目起到了不小的作用，使本人感到本科生活没有完全丧失希望。昨日翻看电脑资料，又看到了这个项目，感慨万千，遂整理后挂在此blog。
{: .prompt-info}

## 1 理论基础（1）——各向异性色散与界面反射

### 1.1 波矢与频率的关系

考虑简谐波 $\boldsymbol{E} = \boldsymbol{E}_0 \mathrm{e}^{\mathrm{i}(\omega t - \boldsymbol{k} \cdot \boldsymbol{r})}, \boldsymbol{B} = \boldsymbol{B}_0 \mathrm{e}^{\mathrm{i}(\omega t - \boldsymbol{k} \cdot \boldsymbol{r})}$ ，代入麦克斯韦方程：

$$
\left\{
\begin{array}{l}
    \nabla \cdot \boldsymbol{D} = 0 \\
    \nabla \times \boldsymbol{E} = - \dfrac{\partial \boldsymbol{B}}{\partial t} \\
    \nabla \cdot \boldsymbol{B} = 0 \\
    \nabla \times \boldsymbol{H} = \dfrac{\partial \boldsymbol{D}}{\partial t}
\end{array}
\right.
\Rightarrow
\left\{
\begin{array}{l}
    \boldsymbol{k} \cdot \boldsymbol{D} = 0 \\
    \boldsymbol{k} \times \boldsymbol{E} = \omega \boldsymbol{B} \\
    \boldsymbol{k} \cdot \boldsymbol{B} = 0 \\
    \boldsymbol{k} \times \boldsymbol{H} = - \omega \boldsymbol{D}
\end{array}
\right.
$$

一般来说，相对磁导率 $\mu = 1$ ，故可得：

$$
\left\{
\begin{array}{l}
    \boldsymbol{k} \times (\boldsymbol{k} \times \boldsymbol{E})
    = (\boldsymbol{k} \cdot \boldsymbol{E}) \boldsymbol{k} - k^2 \boldsymbol{E} \\
    \boldsymbol{k} \times (\boldsymbol{k} \times \boldsymbol{E})
    = \omega \boldsymbol{k} \times (\mu_0 \boldsymbol{H})
    = - \omega^2 \mu_0 \boldsymbol{D} \\
\end{array}
\right.
$$

$$
\Rightarrow
\boldsymbol{D}
= \frac{k^2 \boldsymbol{E} - (\boldsymbol{k} \cdot \boldsymbol{E}) \boldsymbol{k}}{\omega^2 \mu_0}
$$

记 $n = \dfrac{kc}{\omega} \quad \hat{\boldsymbol{k}} = \dfrac{\boldsymbol{k}}{k} = (\hat{k}_x, \hat{k}_y, \hat{k}_z) \quad \zeta = \hat{\boldsymbol{k}} \cdot \boldsymbol{E}$ ，则：

$$
\boldsymbol{D} = \varepsilon_0 n^2 (\boldsymbol{E} - \zeta \hat{\boldsymbol{k}}) = \varepsilon_0 \boldsymbol{\varepsilon} \cdot \boldsymbol{E}
$$

认为相对介电常数张量 $\boldsymbol{\varepsilon}$ 是对角化的，即 $\boldsymbol{\varepsilon} = \text{diag}(\varepsilon_x, \varepsilon_y, \varepsilon_z)$ ，于是得：

$$
n^2 (E_i - \zeta \hat{k}_i) = \varepsilon_i E_i
$$

$$
\Rightarrow
\zeta
= \dfrac{1 - \dfrac{\varepsilon_i}{n^2}}{\hat{k}_i} E_i
$$

**若 $\zeta = 0$ ，则：**

$$
\varepsilon_x = \varepsilon_y = \varepsilon_z = n^2
$$

即退化到各向同性情况，显然有：

$$
\boxed{
    k^2 = \frac{\varepsilon \omega^2}{c^2}
}
$$

**若 $\zeta \neq 0$ ，则：**

$$
\zeta
= {\sum_j \hat{k}_j E_j}
= \sum_j \dfrac{\hat{k}_i^2}{1 - \dfrac{\varepsilon_i}{n^2}} \zeta \\
$$

$$
\Rightarrow
\sum_i \frac{\hat{k}_i^2}{1 - \dfrac{\varepsilon_i}{n^2}}
= 1
$$

上式可写作：

$$
\boxed{
    \sum_i \frac{\hat{k}_i^2}{1 - \dfrac{\varepsilon_i}{n^2}} = 1
}
\quad 或 \quad
\boxed{
    \sum_i \frac{\hat{k}_i^2}{\dfrac{n^2}{\varepsilon_i} - 1} = 0
}
$$

若光只在XOZ平面传播， $k_y = 0$ ，则可得：

$$
\boxed{
    \varepsilon_x k_x^2 + \varepsilon_z k_z^2 = \frac{\omega^2 \varepsilon_x \varepsilon_z}{c^2}
}
$$

### 1.2 界面反射系数

<img src="{{'/assets/img/2026/2026-07-31-near-field-optics-init/Rp.png' | relative_url}}"
    alt="Rp"
    style="display:block; margin:0 auto; max-width:50%; height:auto;">

**考虑 $p$ 波**，此时 $E_y = 0$ ，有边界条件：

$$
\boldsymbol{n} \times (\boldsymbol{E_1} - \boldsymbol{E_2}) = 0 \quad
\boldsymbol{n} \times (\boldsymbol{H_1} - \boldsymbol{H_2}) = 0
$$

$$
\Rightarrow
\left\{
\begin{array}{l}
    E_{Ix} + E_{Rx} = E_{Tx} \\
    H_{Iy} + H_{Ry} = H_{Ty}
\end{array}
\right.
$$

又由 $\boldsymbol{k} \times \boldsymbol{H} = - \omega \boldsymbol{D} \quad \boldsymbol{k} \times \boldsymbol{E} = \omega \boldsymbol{B}$ ，得：

$$
\left\{
\begin{array}{l}
    \omega D_x = k_z H_y \\
    \omega D_y = k_x H_z - k_z H_x \\
    \omega D_z = - k_x H_y \\
    \omega B_x = k_z E_y \\
    \omega B_y = - k_x E_z + k_z E_x \\
    \omega B_z = k_x E_y
\end{array}
\right.

\Rightarrow
\left\{
\begin{array}{l}
    H_y
    = \dfrac{\varepsilon_x}{k_z} \varepsilon_0 \omega E_x
    = - \dfrac{\varepsilon_z}{k_x} \varepsilon_0 \omega E_z \\
    H_x = H_z = 0 \\
    \varepsilon_x k_x^2 + \varepsilon_z k_z^2 = \dfrac{\omega^2 \varepsilon_x \varepsilon_z \mu_y}{c^2}
\end{array}
\right.
$$

故：

$$
\frac{\varepsilon_{1x}}{k_{1z}} E_{Ix} - \frac{\varepsilon_{1x}}{k_{1z}} E_{Rx}
= \frac{\varepsilon_{2x}}{k_{2z}} E_{Tx}
= \frac{\varepsilon_{2x}}{k_{2z}} (E_{Ix} + E_{Rx})
$$

由上便可得：

$$
\boxed{
    R_{p12}
    = \frac{E_{R}}{E_{I}}
    = \frac{E_{Rx}}{E_{Ix}}
    = \frac{\dfrac{k_{2z}}{\varepsilon_{2x}} - \dfrac{k_{1z}}{\varepsilon_{1x}}}{\dfrac{k_{2z}}{\varepsilon_{2x}} + \dfrac{k_{1z}}{\varepsilon_{1x}}}
}
$$

**再考虑 $s$ 波**，此时 $E_x = E_z = 0$ ，有边界条件：

$$
\boldsymbol{n} \times (\boldsymbol{E_1} - \boldsymbol{E_2}) = 0 \quad
\boldsymbol{n} \times (\boldsymbol{H_1} - \boldsymbol{H_2}) = 0
$$

$$
\Rightarrow
\left\{
\begin{array}{l}
    E_{Iy} + E_{Ry} = E_{Ty} \\
    H_{Ix} + H_{Rx} = H_{Tx}
\end{array}
\right.
$$

又由 $\boldsymbol{k} \times \boldsymbol{H} = - \omega \boldsymbol{D} \quad \boldsymbol{k} \times \boldsymbol{E} = \omega \boldsymbol{B}$ ，得：

$$
\left\{
\begin{array}{l}
    \omega D_x = k_z H_y \\
    \omega D_y = k_x H_z - k_z H_x \\
    \omega D_z = - k_x H_y \\
    \omega B_x = - k_z E_y \\
    \omega B_y = - k_x E_z + k_z E_x \\
    \omega B_z = k_x E_y
\end{array}
\right.

\Rightarrow
\left\{
\begin{array}{l}
    H_x = - k_z \dfrac{1}{\omega \mu_0 \mu_x} E_y \\
    H_y = 0 \\
    H_z = k_x \dfrac{1}{\omega \mu_0 \mu_z} E_y \\
    \mu_x k_x^2 + \mu_z k_z^2 = \dfrac{\omega^2 \mu_x \mu_z \varepsilon_y}{c^2}
\end{array}
\right.
$$

故：

$$
k_{1z} E_{Iy} - k_{1z} E_{Ry}
= k_{2z} E_{Ty}
= k_{2z} (E_{Iy} + E_{Ry})
$$

由上便可得：

$$
\boxed{
    R_{s12}
    = \frac{E_{R}}{E_{I}}
    = \frac{E_{Ry}}{E_{Iy}}
    = \frac{k_{1z} - k_{2z}}{k_{1z} + k_{2z}}
}
$$

此外，还有：

$$
\boxed{
    R_{12} = - R_{21} \qquad
    R_{12}^2 + T_{12} T_{21} = 1
}
$$

### 1.3 近场近似

电磁波电场满足亥姆霍兹方程 $\dfrac{\partial^2 E_\alpha}{\partial x_{\alpha}^2} - \dfrac{1}{c^2} \dfrac{\partial^2 (\varepsilon_\alpha E_\alpha)}{\partial t^2} = 0$ （来自 $\nabla^2\boldsymbol{E} = \mu_0 \dfrac{\partial^2 \boldsymbol{D}}{\partial t^2}$ ） 。由于材料较小，推迟效应可略，这等价于让亥姆霍兹方程中的光速趋于无穷。此时方程化为拉普拉斯方程 $\dfrac{\partial^2 E_\alpha}{\partial x_{\alpha}^2} = 0$ ，故可以定义电势。

近场近似下，只有 $p$ 波电场，没有磁场（参考： $\boldsymbol{B} = \dfrac{\boldsymbol{k}}{\omega} \times \boldsymbol{E}$ ）。入射场和反射场可以用电势 $\phi(r,t)$ 来描述。我们把电势写为：

$$
\boxed{
    \phi_i(r,t)
    = \mathrm{e}^{-\mathrm{i} \omega t} (\phi_{i \uparrow} \mathrm{e}^{-\mathrm{i} qx - qz} + \phi_{i \downarrow} \mathrm{e}^{-\mathrm{i} qx + qz})
}
$$

这里 $k_z = \pm i q$ ，可由拉普拉斯方程得到。

考虑材料界面的反射，边界条件为：

$$
\left\{
    \begin{array}{l}
        E_{1x} = E_{2x} \\
        E_{1z} - E_{2z}
        = \dfrac{\rho_{2D}}{\varepsilon_0}
        = \dfrac{q j_{2D}}{\omega \varepsilon_0}
        = \dfrac{q \sigma E_{1x}}{\omega \varepsilon_0}
    \end{array}
\right.
\Rightarrow
\left\{
    \begin{array}{l}
        \phi_{1 \uparrow} + \phi_{1 \downarrow} = \phi_{2 \uparrow} + \phi_{2 \downarrow} \\
        (q \phi_{1 \uparrow} − q \phi_{1 \downarrow}) − (q \phi_{2 \uparrow} − q \phi_{2 \downarrow})
        = - \dfrac{i q^2 \sigma}{\omega \varepsilon_0} (\phi_{1 \uparrow} + \phi_{1 \downarrow})
    \end{array}
\right.
$$

上式也可以写成矩阵形式：

$$
\begin{pmatrix}
    1 & 1 \\
    q + \dfrac{i q^2 \sigma}{\omega \varepsilon_0} & - q + \dfrac{i q^2 \sigma}{\omega \varepsilon_0}
\end{pmatrix}
\begin{pmatrix}
    \phi_{1 \uparrow} \\
    \phi_{1 \downarrow}
\end{pmatrix}
=
\begin{pmatrix}
    1 & 1 \\
    q & -q
\end{pmatrix}

\begin{pmatrix}
    \phi_{2 \uparrow} \\
    \phi_{2 \downarrow}
\end{pmatrix}
$$

解得：

$$
\begin{pmatrix}
    \phi_{1 \uparrow} \\
    \phi_{1 \downarrow}
\end{pmatrix}
=
\begin{pmatrix}
    1-\dfrac{i q \sigma}{2 \omega \varepsilon_0} & -\dfrac{i q \sigma}{2 \omega \varepsilon_0} \\
    \dfrac{i q \sigma}{2 \omega \varepsilon_0} & 1 + \dfrac{i q \sigma}{2 \omega \varepsilon_0}
\end{pmatrix}
\begin{pmatrix}
    \phi_{2 \uparrow} \\
    \phi_{2 \downarrow}
\end{pmatrix}
=:
\hat{M}
\begin{pmatrix}
    \phi_{2 \uparrow} \\
    \phi_{2 \downarrow}
\end{pmatrix}
$$

令 $\phi_{2 \uparrow} = 0$ ，则有：

$$
\boxed{
    \varepsilon_z
    = \frac{E_{1z}}{E_{2z}}
    = 1 + \frac{i q \sigma}{\omega \varepsilon_0}
}
$$

$$
\boxed{
    R_p
    = \frac{\phi_{1 \uparrow}}{\phi_{1 \downarrow}}
    = \frac{- \dfrac{i q \sigma}{2 \omega \varepsilon_0}}{1 + \dfrac{i q \sigma}{2 \omega \varepsilon_0}}
    = \frac{1 - \varepsilon_z}{1 + \varepsilon_z}
}
$$

另外，对于薄片材料：

$$
\begin{pmatrix}
    \phi_{1 \uparrow} \\
    \phi_{1 \downarrow}
\end{pmatrix}
= \hat{M}
\begin{pmatrix}
    \phi_{2 \uparrow} \\
    \phi_{2 \downarrow}
\end{pmatrix}
= \hat{M}
\begin{pmatrix}
    \mathrm{e}^{-qd} & 0 \\
    0 & \mathrm{e}^{qd}
\end{pmatrix}
\hat{M}^{-1}
\begin{pmatrix}
    \phi_{3 \uparrow} \\
    \phi_{3 \downarrow}
\end{pmatrix}
$$

若极化函数非局部，或者更不幸地，与 $k_z$ 有关，需修正如下：

$$
\left\{
    \begin{array}{l}
        E_{1x} = E_{2x} \\
        D_{1z} = D_{2z}
    \end{array}
\right.
\Rightarrow
\left\{
    \begin{array}{l}
        \phi_{1 \uparrow} + \phi_{1 \downarrow} = \phi_{2 \uparrow} + \phi_{2 \downarrow} \\
        i q (\phi_{1 \uparrow} − \phi_{1 \downarrow}) = \varepsilon_z k_z (\phi_{2 \uparrow} − \phi_{2 \downarrow})
    \end{array}
\right.
$$

令 $\phi_{2 \uparrow} = 0$ ，则有：

$$
\boxed{
    R_p
    = \frac{\phi_{1 \uparrow}}{\phi_{1 \downarrow}}
    = \frac{iq - k_z \varepsilon_z(\omega,q,k_z)}{iq + k_z \varepsilon_z(\omega,q,k_z)}
}
$$

### 1.4 厚度均匀材料的反射系数

<img src="{{'/assets/img/2026/2026-07-31-near-field-optics-init/Rpslab.png' | relative_url}}"
    alt="Rpslab"
    style="display:block; margin:0 auto; max-width:50%; height:auto;">

根据图中标记的光波成分，可以直接写出：

$$
\left\{
    \begin{array}{l}
        \varphi = k_z d \\
        E_{D1} = T_{p12} E_I + \mathrm{e}^{\mathrm{i} \varphi} R_{p21} E_{D2} \\
        E_{D2} = \mathrm{e}^{\mathrm{i} \varphi} R_{p23} E_{D1} \\
        E_{R} = R_{p12} E_I + \mathrm{e}^{\mathrm{i} \varphi} T_{p21} E_{D2}    
    \end{array}
\right.
$$

$$
\Rightarrow
\boxed{
    R_{pslab}
    = \frac{E_R}{E_I}
    = \frac{R_{p12} + \mathrm{e}^{2 \mathrm{i} k_z d} R_{p23}}{1 - \mathrm{e}^{2 \mathrm{i} k_z d} R_{p21
} R_{p23}}
}
$$

### 1.5 反射系数虚部的意义

$R_p$ 的虚部正比于电磁场对系统的做功（光吸收）。虚部-频率函数如果有峰，意味着在对应的频率，材料有本征模式（collective mode），吸收能量最大。

## 2 理论基础（2）——固体介电响应模型

### 2.1 固体极化模型

处于基态的原子没有偶极矩。然而，当施加电场 $\boldsymbol{E}$ 时，原子内正电荷和负电荷的相对位移会产生感应偶极矩。 $\boldsymbol{E}$ 的大小较小时，有：

$$
\boldsymbol{p}_{\text{ind}} = \alpha \boldsymbol{E}
$$

其中 $\alpha$ 称为原子极化率。

假设固体样品为椭球体。施加的外电场 $\boldsymbol{E}_0$ 是距离样品很远时的电场值。椭球体内的宏观场由 $\boldsymbol{E} = \boldsymbol{E}_0 − \lambda \boldsymbol{P} = \boldsymbol{E}_0 +\boldsymbol{E}_1$ 给出。

场 $\boldsymbol{E}_1 = − \lambda \boldsymbol{P}$ 称为去极化场， $\lambda$ 称为去极化因子。对于沿三个主轴的去极化因子 $\lambda_1, \lambda_2, \lambda_3$ ，有：

$$
\lambda_1 + \lambda_2 + \lambda_3 = \frac{1}{\varepsilon_0}
$$

假设我们知道固体内部的宏观场 $\boldsymbol{E}$。考虑位置 $\boldsymbol{r}$ 处的原子。围绕 $\boldsymbol{r}$ 画一个半径为 $l$ 的球体（称为洛伦兹球）， $l$ 需远大于原子间距 $a$ 。其他原子上的感应偶极子对 $\boldsymbol{r}$ 处电场的贡献可以分为两部分：


1. 球外的原子，我们可以宏观地处理其贡献，将它们视为具有极化强度 $\boldsymbol{P}$ 的连续体的一部分。此时球内势场为：
   
    $$
    \begin{align*}
        \phi(\boldsymbol{r})
        &= \int \mathrm{d}^3 r' \frac{\boldsymbol{P}(\boldsymbol{r'}) \cdot (\boldsymbol{r} - \boldsymbol{r'})}{4 \pi \varepsilon_0 |\boldsymbol{r} - \boldsymbol{r'}|^3} \\
        &= \int \mathrm{d}^3 r' \frac{1}{4 \pi \varepsilon_0} \left(\nabla' \cdot \left[\frac{\boldsymbol{P}(\boldsymbol{r'})}{|\boldsymbol{r} - \boldsymbol{r'}|}\right] - \frac{\nabla' \cdot \boldsymbol{P}(\boldsymbol{r'})}{|\boldsymbol{r} - \boldsymbol{r'}|} \right) \\
        &= \oint \frac{1}{4 \pi \varepsilon_0} \frac{\boldsymbol{P}(\boldsymbol{r'}) \cdot \mathrm{d}\boldsymbol{S}'}{|\boldsymbol{r} - \boldsymbol{r'}|} \text{（利用椭球体内极化均匀的性质）}
    \end{align*}
    $$

    $$
    \begin{align*}
        \Rightarrow
        \boldsymbol{E}_2
        &= - \nabla \phi(\boldsymbol{r}) \\
        &= \int_S \frac{1}{4 \pi \varepsilon_0} \mathrm{d} S' \, \boldsymbol{P}(\boldsymbol{r}') \cdot \boldsymbol{n}(\boldsymbol{r}') \frac{\boldsymbol{r} - \boldsymbol{r}'}{|\boldsymbol{r} - \boldsymbol{r}'|^3} \\
        &= - \hat{\boldsymbol{P}} \int_{\theta = 0}^{\theta = \pi} \frac{1}{2 \varepsilon_0} l^2 \mathrm{d} (\cos \theta) P \cos \theta \frac{l \cos \theta}{l^3} \\
        &= \frac{\boldsymbol{P}}{3 \varepsilon_0}
    \end{align*}
    $$

2. 球内的原子，我们可以计算它们各自的偶极矩 $\boldsymbol{p}_i$ 的贡献。

    $$
    \boldsymbol{E}_3
    = \sum_i \frac{1}{4 \pi \varepsilon_0} \frac{3(\boldsymbol{p}_i \cdot \boldsymbol{r}_i)\boldsymbol{r}_i - r_i^2 \boldsymbol{p}_i}{r_i^5} \\
    = \frac{p}{4 \pi \varepsilon_0} \sum_i \frac{3z_i^2 - r_i^2}{r_i^5} \hat{\boldsymbol{z}}
    $$

对立方对称晶体， $\boldsymbol{E}_3 = 0$ ，从而：

$$
\boxed{
    \boldsymbol{E}_{LF} = \boldsymbol{E}_0 + \boldsymbol{E}_1 + \boldsymbol{E}_2 + \boldsymbol{E}_3 = \boldsymbol{E} + \frac{\boldsymbol{P}}{3 \varepsilon_0}
}
$$

> 对球形样品， $\boldsymbol{E}_1 = - \dfrac{\boldsymbol{P}}{3 \varepsilon_0}$ ，故：
> 
> $$
\boldsymbol{E}^{sphere}_{LF} = \boldsymbol{E}_0
> $$

由此便可得克劳修斯-莫索提关系：

$$
\begin{align*}
    & \boldsymbol{P}
    = N \boldsymbol{p}
    = N \alpha (\boldsymbol{E} + \frac{\boldsymbol{P}}{3 \varepsilon_0}) \\
    \Rightarrow
    & \boldsymbol{P}
    = \frac{N \alpha}{1 - \dfrac{N \alpha}{3 \varepsilon_0}} \boldsymbol{E} =: \chi \boldsymbol{E} \\
    \Rightarrow
    & \varepsilon
    = 1 + \frac{\dfrac{N \alpha}{\varepsilon_0}}{1 - \dfrac{N \alpha}{3 \varepsilon_0}} \\
    \Rightarrow &
    \boxed{
        \frac{\varepsilon - 1}{\varepsilon + 2}
        = \frac{N \alpha}{3 \varepsilon_0}
    }
\end{align*}
$$

### 2.2 原子极化率的分析

原子极化率可能包括电子、离子和偶极子取向的贡献，有：

$$
\alpha = \alpha_{e} + \alpha_{\text{ion}} + \alpha_{\text{dipole}}
$$

其中 $\alpha_{e}, \alpha_{\text{ion}}$ 几乎不随温度变化

#### 2.2.1 偶极子取向

在没有电场的情况下，偶极子 $\boldsymbol{p}$ 在立体角 $\mathrm{d} \Omega = \sin \theta \mathrm{d} \theta \mathrm{d} \phi$ 内的概率为 $\dfrac{\mathrm{d} \Omega}{4 \pi}$ ，与 $\theta, \phi$ 无关。在电场为 $\boldsymbol{E}$ 的情况下，偶极子 $\boldsymbol{p}$ 在立体角 $\mathrm{d} \Omega$ 内的概率与 $\mathrm{d} Ω \; \mathrm{e}^{- \frac{W}{k_B T}}$ 成正比，其中 $W = −\boldsymbol{p} \cdot \boldsymbol{E}$ 是场 $\boldsymbol{E}$ 中偶极子的能量。取平行于 $\boldsymbol{E}$ 的方向为 $z$ 方向，则 $p_x, p_y$ 的平均值显然为零，我们有：

$$
\bar{p}_z
= \frac{\int \mathrm{d} \Omega \; \mathrm{e}^\frac{pE \cos \theta}{k_B T} p \cos \theta}{\int \mathrm{d} \Omega \; \mathrm{e}^\frac{pE \cos \theta}{k_B T}}
$$

记 $x = \cos \theta, \xi = \dfrac{pE}{k_B T}$ ，则：

$$
\bar{p}_z
= p \frac{\int_{-1}^1 \mathrm{d} x \; x \mathrm{e}^{\xi x}}{\int_{-1}^1 \mathrm{d} x \; \mathrm{e}^{\xi x}}
= p \frac{\mathrm{d}}{\mathrm{d} \xi} \left( \ln \int_{-1}^1 \mathrm{d}x \; \mathrm{e}^{\xi x} \right)
$$

$$
\Rightarrow
\boxed{
    \bar{p}_z
    = p \left(\coth \xi - \frac{1}{\xi}\right) =: p \mathcal{L}(\xi)
}
$$

当 $\xi \to \infty$ 时， $\mathcal{L}(\xi) \to 1$ 。
 
当 $\xi \to 0$ 时， $\mathcal{L}(\xi) \to \dfrac{\xi}{3}$ ，此时：

$$
\bar{p}_z = \frac{p^2}{3 k_B T} E
\Rightarrow
\boxed{
    \alpha_{\text{dipole}} = \frac{p^2}{3 k_B T}
}
$$

#### 2.2.2 电子

采用受迫振荡模型：

$$
m \ddot{\boldsymbol{r}}
= -k \boldsymbol{r} - \frac{m \dot{\boldsymbol{r}}}{\tau} - e \boldsymbol{E}
$$

$$
\Rightarrow
\boldsymbol{r}
= \frac{- \dfrac{e \boldsymbol{E}}{m}}{- \omega^2 + \dfrac{i \omega}{\tau} + \omega_0^2}
= \frac{\boldsymbol{p}}{-e}
$$

故：

$$
\boxed{
    \alpha_e = \frac{\dfrac{e^2}{m}}{- \omega^2 + \dfrac{i \omega}{\tau} + \omega_0^2}
}
$$

对金属材料，可以取 $\omega_0 = 0$ 。

#### 2.2.3 离子

依然采用受迫振荡模型，但不计入阻尼：

$$
\left\{
\begin{array}{l}
    M_+ \ddot{u}_+
    = - k (u_+ - u_-) + z e E_{LF} \\
    M_- \ddot{u}_-
    = k (u_+ - u_-) - z e E_{LF} \\
    E_{LF}
    = E + \dfrac{P}{3 \varepsilon_0} \\
    P = \dfrac{ze}{V}(u_+ - u_-) + \dfrac{1}{V} (\alpha_+ + \alpha_-) E_{LF} \text{（离子偏移、离子本身极化）}
\end{array}
\right.
$$

$$
\Rightarrow
r := u_+ - u_-
= - \frac{ze}{\beta \bar{M}} (\omega^2 - \omega_T^2)^{-1} E
$$

其中：

$$
\begin{cases}
    \beta = 1 - \dfrac{1}{3 \varepsilon_0} \dfrac{\alpha_+ + \alpha_-}{V} \\
    \bar{M} = (M_+^{-1} + M_-^{-1})^{-1} \\
    \omega_T^2 = \Omega_+^2 + \Omega_-^2 - \dfrac{\Omega_{p+}^2 + \Omega_{p-}^2}{3 \beta} \\
    \Omega_{\pm}^2 = \dfrac{k}{M_\pm} \\
    \Omega_{p \pm}^2 = \dfrac{z^2 e^2}{\varepsilon_0 V M_\pm}
\end{cases}
$$

进一步，可得：

$$
P
= \left( b_{22} - \frac{b_{12}^2}{\omega^2 - \omega_T^2} \right) E
$$

$$
\Rightarrow
\boxed{
    \chi(\omega)
    = b_{22} - \frac{b_{12}^2}{\omega^2 - \omega_T^2}
}
$$

其中：

$$
b_{22} = \dfrac{\alpha_+ + \alpha_-}{\beta V} \quad b_{12}^2 = \dfrac{z^2 e^2}{\beta^2 \bar{M} V}
$$

注意到 $\chi_\infty = b_{22},\chi_O = b_{22} + \dfrac{b_{12}^2}{\omega_T^2} \Rightarrow b_{12}^2 = \omega_T^2(\chi_O - \chi_\infty) = {\omega_T^2} (\varepsilon_O - \varepsilon_\infty)$ ，故：

$$
\varepsilon(\omega)
= \varepsilon_\infty - \frac{ {\omega_T^2} (\varepsilon_O - \varepsilon_\infty)}{\omega^2 - \omega_T^2}
$$

记 $\omega_L^2 = \omega_T^2 \dfrac{\varepsilon_O}{\varepsilon_\infty}$ ，则：

$$
\boxed{
    \varepsilon(\omega)
= \varepsilon_\infty \frac{\omega^2 - \omega_L^2}{\omega^2 - \omega_T^2}
}
$$

$\omega_L$ 和 $\omega_T$ 是 $TO$ 和 $LO$ 声子频率，且 $\omega_L > \omega_T$

### 2.3 固体中的电磁波

由前，并认为材料各向同性，有：

$$
\left( \frac{\omega^2}{c^2} \varepsilon(\omega) - q^2 \right) \boldsymbol{E} + \boldsymbol{q} (\boldsymbol{q} \cdot \boldsymbol{E}) = 0
$$

不妨取 $q_x = 0$ ，则有：

$$
\Rightarrow
\begin{pmatrix}
    \dfrac{\omega^2}{c^2} \varepsilon(\omega) - q^2 & 0 & 0 \\
    0 & \dfrac{\omega^2}{c^2} \varepsilon(\omega) - q_z^2 & q_y q_z \\
    0 & q_y q_z & \dfrac{\omega^2}{c^2} \varepsilon(\omega) - q_y^2
\end{pmatrix}
\begin{pmatrix}
    E_x \\
    E_y \\
    E_z
\end{pmatrix}
= 0
$$

上式须有解，故得：

$$
\boxed{
    \varepsilon(\omega) \left[ \frac{\omega^2}{c^2} \varepsilon(\omega) - q^2 \right]^2 = 0
}
$$

上式有两解：

- $\varepsilon(\omega) = 0$ ，是纵波模式，此时 $\boldsymbol{q} \parallel \boldsymbol{E}$
- $\dfrac{\omega^2}{c^2} \varepsilon(\omega) = q^2$ ，是横波模式，此时 $\boldsymbol{q} \cdot \boldsymbol{E} = 0$

#### 2.3.1 纵波模式

忽略碰撞，认为 $\tau \to \infty$

(1) $\varepsilon(\omega) = 1 + \dfrac{\dfrac{4 \pi N e^2}{m}}{- \omega^2 + \omega_0^2} = 1 + \dfrac{\omega_p^2}{- \omega^2 + \omega_0^2}$

$$
\Rightarrow
\boxed{
    \omega^2 = \omega_0^2 + \omega_p^2
}
$$

(2) $\varepsilon(\omega) = \varepsilon_\infty \dfrac{\omega^2 - \omega_L^2}{\omega^2 - \omega_T^2}$

$$
\Rightarrow
\boxed{
    \omega = \omega_L
}
$$

#### 2.3.2 横波模式

同样认为 $\tau \to \infty$

(1) $\varepsilon(\omega) = 1 + \dfrac{\omega_p^2}{- \omega^2 + \omega_0^2}$

$$
\Rightarrow
\boxed{
    c^2 q^2 = \omega^2 \left( \frac{\omega_p^2 + \omega_0^2 - \omega^2}{\omega_0^2 - \omega^2} \right)
}
$$

$\omega_0 < \omega < (\omega_p^2 + \omega_0^2)^{\frac{1}{2}}$ 时 $\varepsilon < 0$ ，此时 $q$ 为虚数，电磁波不扩散。

(2) $\varepsilon(\omega) = \varepsilon_\infty \dfrac{\omega^2 - \omega_L^2}{\omega^2 - \omega_T^2}$

$$
\Rightarrow
\boxed{
    c^2 q^2 = \omega^2 \varepsilon_\infty \frac{\omega^2 - \omega_L^2}{\omega^2 - \omega_T^2}
}
$$

$\omega_T < \omega < \omega_L$ 时 $\varepsilon < 0$ ，此时 $q$ 为虚数，电磁波不扩散。$\omega_T, \omega_L$ 之间的区域也被称作reststrahlen区。

> 若在晶体的集体激发中，晶体的结构基元只是作整体平移振动，结构基元内部各原子的相对位置关系不变，则对应的声子称为声学声子，否则称为光学声子。

## 3 实例分析： $\alpha-V_2O_5$

> **INFO**  
>
> 此处的工作内容是作出 $R_{pslab}$ 关于 $\omega, k_x$ 的图像，并解释现象。
{: .prompt-info}

$$
\varepsilon_a(\omega)
= \varepsilon_{a,\infty} \frac{(\omega^a_{LO})^2 - \omega^2 + i \gamma^a \omega}{(\omega^a_{TO})^2 - \omega^2 + i \gamma^a \omega} \quad (a = x, y, z)
$$

$$
k_{sz}^2 + k_x^2 = \frac{\omega^2}{c^2}
$$

$$
\varepsilon_z k_z^2 + \varepsilon_x k_x^2
= \frac{\omega^2 \varepsilon_x \varepsilon_z}{c^2}
$$

$$
R_p
= \frac{\dfrac{k_z}{\varepsilon_x} - k_{sz}}{\dfrac{k_z}{\varepsilon_x} + k_{sz}}
$$

$$
R_{pslab}
= \frac{1-\mathrm{e}^{2 \mathrm{i} k_z d}}{\dfrac{1}{R_p} - R_p \mathrm{e}^{2 \mathrm{i} k_z d}}
$$


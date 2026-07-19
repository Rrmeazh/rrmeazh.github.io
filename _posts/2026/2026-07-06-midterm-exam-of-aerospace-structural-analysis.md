---
title: "飞行器结构力学期中试卷"
date: 2026-07-06 00:00:00 +0800
categories: [Courses, Mechanics]
tags: [Solid Mechanics, Aerospace]
math: true

description: 本文为飞行器结构力学的期中试卷
---

## 0 分数统计

| 题目        | 1-1  | 1-2  | 1-3  | 1-4  | 1-5  | 1-6  | 1-7  | 1-8  | 2     | 3     | 总分    |
| :-------- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :--- | :---- | :---- | :---- |
| **满分**    | 3    | 4    | 2    | 3    | 10   | 6    | 8    | 4    | 21    | 39    | 100   |
| **平均分**   | 2.11 | 1.33 | 1.08 | 0.69 | 4.69 | 4.64 | 3.67 | 0.82 | 14.79 | 19.95 | 53.72 |
| **标准差**   | 0.92 | 1.84 | 0.77 | 0.95 | 1.66 | 1.61 | 1.96 | 1.25 | 7.15  | 12.69 | 20.36 |
| **平均得分率** | 0.70 | 0.33 | 0.54 | 0.23 | 0.47 | 0.77 | 0.46 | 0.21 | 0.70  | 0.51  | 0.54  |

| 总分区间 | [90,100) | [80,90) | [70,80) | [60,70) | <60 |
| :--: | :------: | :-----: | :-----: | :-----: | :-: |
|  人数  |    0     |    6    |    5    |    6    | 22  |

## 1 简答题（40分）

**1-1 请举例说明，在什么情况下飞机的过载系数分别为正值、负值和零？（3分，70%）**

**答：** 水平加速飞行的飞机在水平方向的过载系数为正（1分）。减速着陆的飞机在飞行方向的过载系数为负（1分）。水平匀速飞行的飞机，在水平方向的过载系数为零（1分）。

**1-2 飞机结构设计的思想大致经过哪四个阶段的演变？（4分，33%）**

**答：** 经历了静强度和刚度、疲劳安全寿命、损伤容限和经济寿命（耐久性）四个阶段的演变，并向可靠性设计方向发展。（每个1分）

**1-3 导弹结构的力学分析和飞机结构的力学分析有哪些异同之处？（2分，54%）**

**答：** 火箭和飞机都由加筋薄壁结构组成，所使用的力学分析方法没有本质的区别（1分），但是由于它们的工作状态不同，所受的载荷工况就不相同。（1分）

**1-4 从量级的角度解释，梁的挠度满足什么条件就可以用线性理论进行分析？（3分，23%）**

**答：** 根据梁的平截面假定，$x$ 方向的弯曲应变 $\varepsilon_x = \varepsilon_x^{(0)} - z \dfrac{\partial^2 w}{\partial x^2}$（1分）。中面应变仅由挠度产生：$\varepsilon_x^{(0)} = \dfrac{1}{2} \left( \dfrac{\partial w}{\partial x} \right)^2$（1分）。当 $w \ll h$ 时（至少要求 $w / h < 1 / 5$），$\left< \varepsilon_x^{(0)} \right> \ll \left< z \dfrac{\partial^2 w}{\partial x^2} \right>$，于是可以用线性理论对这些薄壁结构进行分析（1分）。

**1-5 下图中的 A、B 和 C 三种应力蒙皮机翼结构，它们的翼型和外部尺寸都相同，蒙皮和内部结构的材料和厚度也相同。请将三种结构的抗扭刚度和抗弯刚度进行排序。另外，该机翼可以看作固定在机身上的悬臂梁，按薄壁梁理论进行初步分析。按此方法计算得到的弯曲应力在机翼的哪个位置不准确，为什么？（10分，47%）**

![01]({{'/assets/img/2026/2026-07-06-midterm-exam-of-aerospace-structural-analysis/01.png' | relative_url}})

**答：** 在材料和厚度相同的情况下抗扭刚度 $GJ_t = 4 G A_z^2 / \oint \dfrac{ds}{h}$ 只和机翼的横截面积和周长相关，与纵墙个数无关（2分）。另外，桁条中剪应力产生的扭矩可以忽略不计（1分）。所以这三种结构的抗扭刚度几乎相同（1分）。增加纵墙个数和桁条就增加了截面惯性矩，抗弯刚度由高到低依次为 $C > B > A$ （3分）。

在靠近机身的约束端附近（1分）由于主梁和腹板的牵扯作用，导致该处翼板的变形滞后于其它部位翼板，产生剪切滞后现象（1分）。在此部位，梁弯曲的平截面假设不再成立（1分），计算得到的弯曲应力就不再准确。

**1-6 运输机的机身可以看作剪切模量为 $G$ 、半径为 $R$ 、壁厚为 $h$ 的薄壁圆筒。为什么在打开货舱舱门时其扭转刚度会降低？请根据相关理论定性说明，在不改变蒙皮材料和机身截面形状的前提下，采取什么措施可以增加打开货舱舱门时机身的扭转刚度？（6分，77%）**

**答：** 货仓处的机身在舱门关闭时是闭口薄壁杆件，其自由扭转刚度为 $2G \pi R^3 h$（1分）。舱门打开时是开口薄壁杆件，其自由扭转刚度为 $2G \pi R h^3$（1分）。可见相对于闭口杆，开口杆的自由扭转刚度会显著下降（1分）。

开口杆的约束扭转刚度为 $E I_\omega^{\*}$ ，其中：$I_\omega^{*}=\int_0^{S_k} \omega^2 h\,ds + \sum_{i=1}^{K}\dfrac{E_i}{E}A_i\omega_i^2$ （1分）。由此可知在蒙皮材料不变（$E$ 不变）和机身截面形状不变（$h$ 和 $\omega$ 的分布不变）（1分）的前提下，只有在座舱开口处增加一些加强筋（增加 $\dfrac{E_i}{E}A_i$ 部分），才能提高其抗扭刚度（1分）。

**1-7 方形截面机身的装载效率优于圆形截面的机身。但为什么机身截面通常是圆形的？假设机身由半径为 $R$、厚度为 $h$ 的圆柱壳和两端的封头组成。在封头和圆柱壳连接处的弯曲应力沿圆柱壳轴线方向按怎样的规律变化？其影响范围大约是多少？通常采取什么措施来防止该连接处发生局部破坏后导致灾难性后果？（8分，46%）**

**答：** 从承力特性来看，内压作用下方形机身壁中存在较大的弯曲应力（1分），它沿壁厚线性分布，没有充分利用材料（1分）。而圆形机身壁中绝大部分区域只存在薄膜应力（1分），它沿壳厚均匀分布，可以充分利用所有的材料（1分），从而达到轻质高强的效果。

封头和圆柱壳连接处的弯曲应力沿轴线方向呈指数衰减（1分），影响范围大约为 $5 \sqrt{Rh}$ 量级（1分）。为了防止局部破坏导致的整体垮塌（1分），可以引入加强筋来把局部破坏造成的影响隔离在有限的范围内（1分），增加了结构的可靠性。

**1-8 图中的两种飞机都采用了双机身构型，但 F82 的水平尾翼与两个机身相连。请从扭转剪应力的分布规律来简单估计 F82 的水平尾翼能否显著提高机身的扭转刚度？（4分，21%）**

**答：** F82 的水平尾翼和垂直尾翼部分可被近似看作 H 形截面的杆件（1分），水平尾翼相当于腹板（1分）。由于 H 杆件腹板的剪应力为零（扇性坐标为零）（1分），所以水平尾翼对抗扭几乎没有贡献（1分）。

## 2 计算题I（21分，70%）

DiskSat 卫星的半径为 $R$、厚度为 $h$、弹性模量为 $E$、泊松比为 $\nu$、密度为 $\rho$。在发射阶段可将它看作一块周边简支的圆形平板进行概要分析。假设火箭以过载系数 $n$ 加速上升，试求：

1. 板的最大挠度的位置和大小
2. 板中最大正应力的位置和大小
3. 板中最大剪应力的位置和大小

提示：剪力 $Q_r = -D \dfrac{\mathrm{d}}{\mathrm{d}r} \left( \dfrac{\mathrm{d}^2w}{\mathrm{d}r^2} + \dfrac{\mathrm{d}w}{r\mathrm{d}r} \right)$ ，弯矩 $M_r = -D \left( \dfrac{\mathrm{d}^2w}{\mathrm{d}r^2} + \nu \dfrac{\mathrm{d}w}{r\mathrm{d}r} \right)$ ， $D = \dfrac{Eh^3}{12(1-\nu^2)}$ , $M_\theta = -D \left( \dfrac{\mathrm{d}w}{r\mathrm{d}r} + \nu \dfrac{\mathrm{d}^2w}{\mathrm{d}r^2} \right)$，正应力 $\sigma_r = \dfrac{M_r z}{h^3/12}$、$\sigma_\theta = \dfrac{M_\theta z}{h^3/12}$，剪应力 $\tau_{rz} = \dfrac{3Q_r}{2h}\left( 1 - \dfrac{4z^2}{h^2} \right)$。

**解：** 作用在圆板上的分布力为：$p = -n\rho gh$ (1分)

通解为：$w = Ar^2 + Br^2 \ln r + C \ln r + K + \frac{pr^4}{64D}$ (2分)

在 $r=0$ 处：

- 挠度有界：$C = 0$ (2分)
- 剪力为零：$Q_r = 0 \Rightarrow \left( \dfrac{4BD}{r} + \dfrac{pr}{2} \right)_{r=0} = 0 \Rightarrow B = 0$ (2分)

在 $r=R$ 处：

- $w = 0 \Rightarrow AR^2 + K + \dfrac{pR^4}{64D} = 0$ (2分)
- $M_r = 0 \Rightarrow \dfrac{\mathrm{d}^2w}{\mathrm{d}r^2} + \nu \dfrac{\mathrm{d}w}{r\mathrm{d}r} = 0 \Rightarrow 2(1+\nu)A + \dfrac{(3+\nu)pR^2}{16D} = 0$ (2分)

可得：$A = -\dfrac{pR^2(3+\nu)}{32D(1+\nu)}$ (1分)     $K = \dfrac{pR^4(5+\nu)}{64D(1+\nu)}$ (1分)

即，挠度为：$w = \dfrac{pR^4}{64D} \left[ \dfrac{(5+\nu)}{(1+\nu)} - \dfrac{2(3+\nu)r^2}{(1+\nu)R^2} + \dfrac{r^4}{R^4} \right]$ (1分)，于是可得：

$M_r = \dfrac{(3+\nu)pR^2}{16} \left[ 1 - \left(\dfrac{r}{R}\right)^2 \right]$ (1分)     $M_\theta = \dfrac{pR^2}{16} \left[ 3+\nu - (1+3\nu)\left(\dfrac{r}{R}\right)^2 \right]$ (1分)

（后部缺失）

## 3 计算题II（39分，51%）

Roll-Out Solar Array 在轨展开后，其桅杆在 $x=0$ 处完全固定在机械臂上，在 $x=L$ 处受到机架对它施加扭矩 $M_x$。桅杆横截面的开口角度沿杆长是变化的。但保守分析时可认为桅杆的横截面沿杆长都是半圆环，其壁厚为 $h$，弹性模量为 $E$，剪切模量为 $G$。试求：

1. 桅杆横截面的主扇性坐标
2. 桅杆横截面的主扇性静矩
3. 桅杆横截面的主扇性惯性矩
4. 桅杆外壁上的扭转剪应力

提示：控制方程 $\theta_x^{IV} - \lambda^2 \theta_x^{''} = m_x / EI_\omega$，$\lambda^2 = D_p / EI_\omega$

![02]({{'/assets/img/2026/2026-07-06-midterm-exam-of-aerospace-structural-analysis/02.png' | relative_url}})

**解：** 由对称性可知，主极点在 $y$ 轴上（1分）。

先以 $o$ 点为极点，开口处为零点（1分），可求扇性坐标：

$$
\omega' = \int_{-\pi/2}^{\theta} R^2 d\theta = R^2 \left( \theta + \frac{\pi}{2} \right) \quad \text{(2分)}
$$

另外：

$$
\int_0^{S_k} \omega' z h ds = \int_{-\pi/2}^{\pi/2} R^4 \left( \theta + \frac{\pi}{2} \right) \sin \theta h d\theta = 2R^4h \quad \text{(2分)}
$$

$$
I_y = \int_{-\pi/2}^{\pi/2} (R \sin\theta)^2 R h d\theta = \frac{\pi R^3 h}{2} \quad \text{(2分)}
$$

所以：

$$
y_c = \frac{\int_0^{S_k} \omega' z h ds}{I_y} = \frac{4R}{\pi} \quad \text{(2分)}
$$

以 $(y_c, 0)$ 为主极点，开口处为零点（1分），可得扇性坐标：

$$
\omega^* = \int_{-\pi/2}^{\theta} (R - y_c \cos\theta) R \mathrm{d}\theta = R^2 \left( \theta + \frac{\pi}{2} \right) - y_c R (\sin\theta + 1) \quad \text{(2分)}
$$

$$\omega_0 = \frac{\int_0^s \omega^* h \mathrm{d}s}{A} = \frac{\int_{-\pi/2}^{\pi/2} \left[ R^2 \left( \theta + \frac{\pi}{2} \right) - y_c R (\sin\theta + 1) \right] R h \mathrm{d}\theta}{\pi R h} = R \left( \frac{\pi}{2}R - y_c \right) \quad \text{(2分)}$$

所以主扇性坐标为：

$$
\omega=\omega^* - \omega_0=R(R\theta-y_c\sin\theta)  \quad \text{(2分)}
$$

于是可得主扇性静矩：

$$
S_\omega=\int_{-\pi/2}^{\theta}R(R\theta-y_c\sin\theta)Rh\,d\theta
=R^3h\left[\frac{1}{2}\left(\theta^2-\frac{\pi^2}{4}\right)+\frac{4}{\pi}\cos\theta\right] \quad \text{(2分)}
$$

主扇性惯性矩：

$$
I_\omega=\int_{-\pi/2}^{\pi/2}R^2(R\theta-y_c\sin\theta)^2Rh\,d\theta
=R^5h\left(\frac{\pi^3}{12}-\frac{8}{\pi}\right) \quad \text{(2分)}
$$

由控制微分方程$\theta_x^{\mathrm{IV}}-\lambda^2\theta_x''=0$ 可得其通解为：

$$
\theta_x=C_0+C_1x+C_2\operatorname{sh}\lambda x+C_3\operatorname{ch}\lambda x \quad \text{(2分)}
$$

由边界条件可以定出其中的常数：

$x = 0$ 时：

$$
\begin{cases}
	\theta_x|_{x=0}=0 \Rightarrow C_0+C_3=0 & \text{(2分)} \\
	\theta_x'|_{x=0}=0 \Rightarrow C_1+C_2\lambda=0 & \text{(2分)}
\end{cases}
$$

$x = L$ 时：

$$
\begin{cases}
	\theta_x''|_{x=L}=0 \Rightarrow C_2\lambda^2\operatorname{sh}\lambda L
+C_3\lambda^2\operatorname{ch}\lambda L=0 & \text{(2分)} \\
	\left. D_p\theta_x'-EI_\omega\theta_x''' \right|_{x=L}=M_x \Rightarrow D_p\left(C_1+C_2\lambda\operatorname{ch}\lambda L+C_3\lambda\operatorname{sh}\lambda L\right)-EI_\omega\lambda^3\left(C_2\operatorname{ch}\lambda L+C_3\operatorname{sh}\lambda L\right)
=M_x & \text{(2分)}
\end{cases}
$$

综上可得：

$$
C_0=
\frac{M_x\operatorname{sh}\lambda L}
{D_p\lambda(1-\operatorname{ch}\lambda L)-EI_\omega\lambda^3}
=
-\frac{M_x\operatorname{th}\lambda L}{D_p\lambda}
$$

$$
C_1=
\frac{-M_x\operatorname{ch}\lambda L}
{D_p(1-\operatorname{ch}\lambda L)-EI_\omega\lambda^2}
=
\frac{M_x}{D_p}
$$

（中间缺失）

$$
D_p = \frac{G \pi R h^3}{3} \quad \text{(1分)}
$$

$$
M_x^{(\omega)} = -EI_\omega \theta''' = -EI_\omega \lambda^3 (C_2 \operatorname{ch} \lambda x + C_3 \operatorname{sh} \lambda x) \quad \text{(1分)}
$$
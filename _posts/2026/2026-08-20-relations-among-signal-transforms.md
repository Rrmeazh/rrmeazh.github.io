---
title: "信号与系统中各种变换的关系"
date: 2026-8-20 00:00:00 +0800
categories: [Courses, Signals and System]
tags: [Signals and System]
math: true

description: 从 FS 与 FT 出发，梳理 LT、ZT、DTFT、DTFS、DFT 与 FFT 的关系。
---

## 0 名词表

| 中文 | English | English abbr. |
| :-- | :-- | :-- |
| 傅立叶级数 | **F**ourier **S**eries | FS |
| 傅立叶变换 | **F**ourier **T**ransform | FT |
| 拉普拉斯变换 | **L**aplace **T**ransform | LT |
| Z变换 | **Z**-**t**ransform | ZT |
| 离散时间傅里叶变换 | **D**iscrete-**t**ime **F**ourier **T**ransform | DTFT |
| 离散时间傅里叶级数 | **D**iscrete-**t**ime **F**ourier **S**eries | DTFS |
| 离散傅里叶变换 | **D**iscrete **F**ourier **T**ransform | DFT |
| 快速傅里叶变换 | **F**ast **F**ourier **T**ransform | FFT |

## 1 FS 与 FT

FS 可以看作是将周期函数（设周期为 $T = \dfrac{2 \pi}{\omega_0}$ ）拆解为基函数之线性组合的一种方法，也可以看作分析频谱成分的计算手段。利用三角函数族 $\\{ \sin n \omega_0 t \\} \cup \\{ \cos n \omega_0 t \\}$ 的正交性，设想 $f(t) = a_0 + \sum_{n = 1}^\infty a_n \cos n \omega_0 t + \sum_{n = 1}^\infty b_n \sin n \omega_0 t$ ，则可以得到：

$$
\begin{align*}
    & \; \quad \int_0^T f(t) \sin m \omega_0 t \, \mathrm{d} t \\
    &= a_0 \int_0^T \sin m \omega_0 t \, \mathrm{d} t + \sum_{n = 1}^\infty a_n \int_0^T \cos n \omega_0 t \sin m \omega_0 t \, \mathrm{d} t + \sum_{n = 1}^\infty b_n \int_0^T \sin n \omega_0 t \sin m \omega_0 t \, \mathrm{d} t \\
    &= b_m \int_0^T \sin^2 m \omega_0 t \, \mathrm{d} t \\
    &= b_m \frac{T}{2}
\end{align*}
$$

$$
\Rightarrow
b_m = \frac{2}{T} \int_0^T f(t) \sin m \omega_0 t \, \mathrm{d} t 
$$

同理也能得到 $a_m$ 的表达式：

$$
a_m = \frac{2}{T} \int_0^T f(t) \cos m \omega_0 t \, \mathrm{d} t \quad (m \neq 0)
$$

$$
a_0 = \frac{1}{T} \int_0^T f(t) \, \mathrm{d} t
$$

借助欧拉公式，亦可以将 FS 整理如下：

$$
f(t) = \sum_{n = -\infty}^\infty F_n \mathrm{e}^{j n \omega_0 t}
\qquad
F_n =
\frac{1}{T} \int_0^T f(t) \mathrm{e}^{-j n \omega_0 t} \, \mathrm{d} t
$$

我们希望像这样的分解可以拓展到非周期函数上。对任意 $f(t)$ ，可以构造一个周期为 $T$ 的函数 $f_T(t)$，使得：

$$
- \frac{T}{2} \leq t < \frac{T}{2} \text{ 时，}f_T(t) = f(t)
$$

那么有：

$$
\begin{align*}
    f_T(t)
    &= \sum_{n = -\infty}^\infty \left( \frac{1}{T} \int_{-\frac{T}{2}}^{\frac{T}{2}} f(t) \mathrm{e}^{-j n \omega_0 t} \, \mathrm{d} t \right) \mathrm{e}^{j n \omega_0 t} \\
    &= \sum_{n = -\infty}^\infty \frac{1}{2 \pi} \left(\int_{-\frac{T}{2}}^{\frac{T}{2}} f(t) \mathrm{e}^{- j \frac{2 \pi n}{T} t} \, \mathrm{d} t \right) \mathrm{e}^{j \frac{2 \pi n}{T} t} \frac{2 \pi}{T}
\end{align*}
$$

对比积分的黎曼和逼进 $\int_{D} G(\omega) \mathrm{d} \omega \approx \sum_{i = 0}^{n - 1} G(\omega_n) \Delta \omega$ ，取 $\omega_n = \dfrac{2 \pi n}{T}, \Delta \omega = \dfrac{2 \pi}{T}, T \to \infty$ ，则有：

$$
G(\omega) = \frac{1}{2 \pi} \left(\int_{-\infty}^{\infty} f(t) \mathrm{e}^{- j \omega t} \, \mathrm{d} t \right) \mathrm{e}^{j \omega t}
\qquad
f(t) = \int_{-\infty}^\infty G(\omega) \mathrm{d} \omega
$$

我们将 $\{ \mathrm{e}^{j \omega t} \}$ 视为基函数。这一套基函数不像周期函数情况中的 $\omega$ 离散取值，是在 $\mathbb{R}$ 上连续取值的。合成原本函数的方式由 FS 中的求和变为了积分，但基函数依然不失正交性。这样就得到了 FT 的正变换与逆变换：

$$
F(\omega) = \int_{-\infty}^{\infty} f(t) \mathrm{e}^{- j \omega t} \, \mathrm{d} t
$$

$$
f(t) = \frac{1}{2 \pi} \int_{-\infty}^\infty F(\omega) \mathrm{e}^{j \omega t} \, \mathrm{d} \omega
$$

$F(\omega)$ 也能像 $a_n, b_n, F_n$ 一样，体现出函数在频率域上的分布。

FT 也可以兼容周期函数，代入 $f(t) = \sum_{n = -\infty}^\infty F_n \mathrm{e}^{j n \omega_0 t}$ ，可以得到：

$$
F(\omega) = \sum_{n = -\infty}^\infty 2 \pi F_n \, \delta (\omega - n \omega_0)
$$

## 2 LT

古典 FT 需要满足绝对可积的条件。广义 FT 须引入冲激函数 $\delta(t)$ ，而且对于指数级增长函数仍无能为力。另外，我们注意到，对实际信号，没有必要/不可能在整个实轴进行 FT 。因此，对 FT 作改造：

- $f(t)$ 乘上 $u(t)$ ，使 $f(t)$ 在 $t < 0$ 的部分补零/充零
- 乘上衰减指数函数 $\mathrm{e}^{- \beta t} \; (\beta > 0)$

就得到了：

$$
\mathcal{F}[f(t) u(t) \mathrm{e}^{-\beta t}]
= \int_0^{+ \infty} f(t) \mathrm{e}^{- (\beta + j \omega) t} \mathrm{d}t
$$

记上式中的 $\beta + j \omega = s$ ，我们就得到了新的变换 LT：

$$
\mathcal{L}[f(t)] = F(s)
= \int_0^{+ \infty} f(t) \mathrm{e}^{- s t} \mathrm{d}t
$$

变换存在的条件即是 $\mathrm{Re}(s) = \beta$ 足够大。

可以看出， LT 相比 FT 延展到了复数域。LT 的收敛域为 $\mathrm{Re}(s) > \beta_0$ 。收敛域的边界总是由系统的奇点决定的。收敛域不能穿过奇点，通常延伸至最右侧的奇点为止。 

根据上面的过程，可以用 FT 的逆变换写出 LT 的逆变换。对任意给定的 $\beta$ ，有：

$$
F(s) = F(\beta + j \omega)
= \int_{- \infty}^{+ \infty} [f(t) u(t) \mathrm{e}^{- \beta t}] \mathrm{e}^{- j \omega t} \mathrm{d} t
$$

故：

$$
f(t) u(t) \mathrm{e}^{- \beta t}
= \frac{1}{2 \pi} \int_{- \infty}^{+ \infty} F(\beta + j \omega) \mathrm{e}^{j \omega t} \mathrm{d} \omega \\
\Rightarrow
f(t) u(t)
= \frac{1}{2 \pi j} \int_{\beta - j \infty}^{\beta + j \infty} F(s) \mathrm{e}^{st} \mathrm{d} s
$$

上式即 LT 逆变换。

LT 逆变换有两种求法。一种是将式子拆分为常见变换结果的组合后查表，另一种是利用留数定理：若 $f(t)$ 的像函数 $F(s)$ 除有限个孤立奇点 $s_1, s_2 \dots s_n$ 外是解析的，且 $\lim_{s \to \infty} F(s) = 0$ ，则：

$$
f(t) = \sum_{k = 1}^n \mathrm{Res} [F(s) \mathrm{e}^{st}, s_k]
$$

除了单边 LT ，有时我们也会遇到双边 LT ：

$$
\mathcal{L}[f(t)]
= \int_{- \infty}^{+ \infty} f(t) \mathrm{e}^{- s t} \mathrm{d}t
$$

在此不作展开。

## 3 ZT

ZT 是 LT 在时域上离散化后的结果。我们在时域上对 $x(t)$ 进行间隔为 $T_s$ 的采样，得到 $x_s(t) = \sum_{n = -\infty}^{\infty} x(n T_s) \delta(t - n T_s)$ 。那么有：

$$
\begin{align*}
    \mathcal{L}[x_s(t)]
    &= \sum_{n = -\infty}^{\infty} x(n T_s) \int_{-\infty}^\infty \delta(t - n T_s) \mathrm{e}^{-s t} \mathrm{d} t \\
    &= \sum_{n = -\infty}^{\infty} x(n T_s) \mathrm{e}^{-s n T_s}
\end{align*}
$$

离散时间信号 $x[n] = x(n T_s)$ 。令：

$$
z = \mathrm{e}^{s T_s}
$$

> 此即 ZT 与 LT 之间转换的关系式

即可得到 ZT 的正变换：

$$
X(z) = \sum_{n = -\infty}^{\infty} x[n] z^{-n}
$$

不难发现上式与洛朗级数形式一样。

> 同理，也可以由单边 LT 推出单边 ZT 。$z$ 域与 $s$ 域之间的关系同上。

对于逆变换，尝试由 LT 入手，会得到：

$$
\begin{align*}
    \sum_{n = -\infty}^{\infty} x[n] \delta(t - n T_s)
    &= \frac{1}{2 \pi j} \int_{\beta - j \infty}^{\beta + j \infty} X(\mathrm{e}^{s T_s}) \mathrm{e}^{st} \mathrm{d}s \\
    &= \frac{1}{2 \pi j} \oint_{C'} \frac{1}{T_s} X(z) z^{\frac{t}{T_s} - 1} \mathrm{d} z \\
\end{align*}
$$

左式有 $\delta$ 函数，而右式的环路路径 $C'$ 是从 $z = \mathrm{e}^{\beta T_s} \mathrm{e}^{- j T_s \infty}$ 到 $z = \mathrm{e}^{\beta T_s} \mathrm{e}^{j T_s \infty}$ 环绕无穷圈。两者之间的关系难以确定。不过我们可以转而从复变函数的角度入手，利用幂函数环路积分的性质：

$$
\oint z^n \mathrm{d}z =
\begin{cases}
    0 & n \neq -1 \\
    2 \pi j & n = -1
\end{cases}
$$

可以直接写出：

$$
x[n] = \frac{1}{2 \pi j} \oint_C X(z) z^{n - 1} \mathrm{d} z
$$

我们知道，单边 LT 的收敛域为直线 $\mathrm{Re}(s) = \beta_0$ 以右的半平面。对于双边 LT ，则还需考虑实轴负半轴的敛散性，收敛域形如为 $r_1 < \mathrm{Re}(s) < r_2$ 。结合变换 $z = \mathrm{e}^{s T_s}$ ，便能确定 ZT 收敛域的形式：

$$
R_1 < |z| < R_2
$$

即圆盘。这和洛朗级数的收敛域形式是一样的。进一步，如果 $x[n]$ 的正序数项/负序数项置零，还能得到其收敛域形式为：

$$
\begin{cases}
    x[n] \text{正序数项置零} & \text{收敛域：} |z| < R \\
    x[n] \text{负序数项置零} & \text{收敛域：} |z| > R
\end{cases}
$$

这个结论可以参考复变函数泰勒展开的收敛域。

## 4 DTFT

上面介绍了 LT 时域离散化的产物 ZT 。对于 FT ，同样可以叠加时域离散化。

在时域上对 $x(t)$ 进行间隔为 $T_s$ 的采样，得到 $x_s(t) = \sum_{n = -\infty}^{\infty} x(n T_s) \delta(t - n T_s)$ 。代入 FT 可得：

$$
\begin{align*}
    \mathcal{F}[x_s(t)]
    &= \sum_{n = -\infty}^{\infty} x(n T_s) \int_{-\infty}^\infty \delta(t - n T_s) \mathrm{e}^{-j \omega t} \mathrm{d} t \\
    &= \sum_{n = -\infty}^{\infty} x(n T_s) \mathrm{e}^{-j \omega n T_s}
\end{align*}
$$

取 $T_s = 1$ 即可得 DTFT 正变换：

$$
X(\mathrm{e}^{j \omega})
= \sum_{n = -\infty}^{\infty} x[n] \mathrm{e}^{-j \omega n}
$$

这里记作 $X(\mathrm{e}^{j \omega})$ 是因为其形式与 ZT 极相似，只是把 $z$ 换成了 $\mathrm{e}^{j \omega}$ 。如果考虑到 $T_s$ 已被设置为 $1$ ，则相当于将 $z = \mathrm{e}^{\beta + j \omega}$ 中的 $\beta$ 置零。而将 LT 中的 $\beta$ 置零，得到的正是 FT 。这一事实进一步证实了这些变换之间的关系。

DTFT 的逆变换可以借助 ZT 写出：

$$
\begin{align*}
    x[n]
    &= \frac{1}{2 \pi j} \oint_C X(\mathrm{e}^{j \omega}) \mathrm{e}^{j (n - 1) \omega} \mathrm{d} (\mathrm{e^{j \omega}}) \\
    &= \frac{1}{2 \pi} \int_{-\pi}^{\pi} X(\mathrm{e}^{j \omega}) \mathrm{e}^{j n \omega} \mathrm{d} \omega
\end{align*}
$$

## 5 从 FT 到 DFT

事实上，我们不可能在无限长的时间区间上连续观测一个真实信号。我们最终得到的，只能是有限时间内、按一定间隔采集的一组数值。相应的，计算方法也从理想的 FT 演化为了 DFT 。这个演化过程依次经历了截断、周期延拓、采样与取主值区间。

设原连续信号为 $f(t)$ ，截取时长为 $T_1 = N T_s$ ，采样周期为 $T_s$ 。以长度为 $T_1$ 的窗函数 $g_{T_1}(t)$ 截取信号：

$$
f_1(t) = f(t) g_{T_1}(t)
$$

由 FT 的乘积性质，时域相乘会在频域形成卷积：

$$
F_1(\omega)
= \frac{1}{2 \pi} F(\omega) * G_{T_1}(\omega)
$$

若 $g_{T_1}(t)$ 为矩形窗，则 $G_{T_1}(\omega)$ 具有主瓣与较大的旁瓣。原信号的频谱会被旁瓣摊开，使本来集中在某些频率处的能量泄漏到邻近频率，这就是频率泄漏现象。增加截取时长可以使主瓣变窄，提高频率分辨能力；改用旁瓣更低的平滑窗可以减轻泄漏，但通常也会使主瓣变宽。二者之间需要按分析目的作出取舍。

然后，将有限长信号 $f_1(t)$ 以 $T_1$ 为周期延拓：

$$
f_p(t) = \sum_{m=-\infty}^{\infty} f_1(t-mT_1)
$$

记基频为 $\omega_1 = \dfrac{2\pi}{T_1}$ ，则周期延拓后的频谱为：

$$
F_p(\omega)
= \omega_1 \sum_{k=-\infty}^{\infty}
F_1(k\omega_1)\delta(\omega-k\omega_1)
$$

这说明周期延拓会把原本连续的频谱离散化。FS 的每一根谱线取自 $F_1(\omega)$ 在 $\omega = k \omega_1$ 处的值。由于只能看到这些等间隔的频率点，真实峰值若落在两根谱线之间，就可能出现栅栏效应。增大 $T_1$ 可以提高频率分辨率。补零也可以增加 DFT 的频率取样点，使已有频谱曲线显示得更细，但不会增加原始观测所包含的信息，也不会提高真正的分辨率。

再以 $T_s$ 为间隔对 $f_p(t)$ 采样，得到周期离散序列：

$$
f_p[n] = f_p(nT_s)
$$

采样角频率为 $\omega_s=\dfrac{2\pi}{T_s}$ 。从连续时间的角度看，采样会使频谱以 $\omega_s$ 为周期重复：

$$
F_s(\omega)
= \frac{1}{T_s}
\sum_{m=-\infty}^{\infty}F_p(\omega-m\omega_s)
$$

如果这些周期延拓的频谱彼此重叠，就会发生频率混叠。因此，采样前应利用抗混叠低通滤波器限制信号带宽，并使采样频率满足 Nyquist 条件。若条件允许，也可以提高采样频率。经过这一步，连续时间周期信号变成周期为 $N$ 的离散时间序列，对应的变换也由 FS 变成了 DFS （离散傅立叶级数）。

周期序列 $f_p[n]$ 的全部信息都包含在任意连续的 $N$ 个样本中。取主值区间：

$$
x[n] = f_p[n] = f_1(n T_s), \quad 0 \leq n \leq N-1
$$

就得到了有限长序列 $x[n]$ 。对这一组数作 DFT ，即可得到加窗信号频谱的线簇近似（关于其近似的进一步叙述见下节）。DFT 的变换公式与 DFS 完全一样。区别在于 DFS 面向的是无限长周期序列，而 DFT 面向的是有限长序列。DFT 等价于先对序列进行周期延拓，再进行 DFS 。若记录首尾不能平滑衔接，这一隐含延拓会在边界制造跳变，这也是实际频谱分析中泄漏的另一种直观解释。

## 6 DTFS, DFT

首先看 DTFS 。对于长度为 $N$ 的序列，我们构造周期为 $N T_s$ 的函数 $x_N(t)$ ，使得：

$$
0 \leq t < N T_s \text{时，}
x_N(t) = \sum_{n = 0}^{N - 1} x(n T_s) \delta(t - n T_s)
$$

代入 FS 变换式，但将 $\dfrac{1}{T}$ 改为 $1$ ，使得形式上与 FT 保持一致：

$$
\begin{align*}
    X_k
    & \stackrel{\mathrm{def}}{=} X \left(\omega_k = \frac{2 \pi k}{N T_s} \right) \\
    &= \sum_{n = 0}^{N - 1} x(n T_s) \int_{-\infty}^\infty \delta(t - n T_s) \mathrm{e}^{-j \frac{2 \pi k}{N T_s} t} \mathrm{d} t \\
    &= \sum_{n = 0}^{N - 1} x(n T_s) \mathrm{e}^{-j \frac{2 \pi n k}{N}}
\end{align*}
$$

此时变换得到的频率结果是离散取值的。能够看出频率分辨率显然为 $\dfrac{1}{N T_s} = \dfrac{f_s}{N}$ 。频率分辨率并不是 $f_s$ 所决定的，$f_s$ 只决定最高可分析频率（Nyquist 定理，$f_{\max} = \dfrac{f_s}{2}$）。

注意到此结果与 ZT 依然极为相似，只是将 $z$ 换成了 $\mathrm{e}^{j \frac{2 \pi k}{N}}$ 。这种变化相当于在 $z$ 域上的单位圆均匀采样 $N$ 个点。

借鉴 FS 中对函数正交性的利用，只不过内积运算由积分变成求和，有：

$$
\begin{align*}
    X_k 
    &= \sum_{m = 0}^{N - 1} x(m T_s) \mathrm{e}^{-j \frac{2 \pi m}{N} k} \\
    \stackrel{W = \mathrm{e}^{j \frac{2 \pi}{N}}}{\Rightarrow}
    X_k W^{nk}
    &= \sum_{m = 0}^{N - 1} x(m T_s) W^{(n-m) k} \\
    \Rightarrow
    \sum_{k = 0}^{N - 1} X_k W^{nk}
    &= \sum_{m = 0}^{N - 1} x(m T_s) \sum_{k = 0}^{N - 1} W^{(n-m) k} \\
    \Rightarrow
    \sum_{k = 0}^{N - 1} X_k W^{nk}
    &= \sum_{m = 0}^{N - 1} x(m T_s) \frac{1 - W^{(n - m) N}}{1 - W^{n - m}} \\
\end{align*}
$$

当 $n = m$ 时 $\dfrac{1 - W^{(n - m) N}}{1 - W^{n - m}} = N$ ，当 $n \neq m$ 时 $\dfrac{1 - W^{(n - m) N}}{1 - W^{n - m}} = 0$ 。故得到 DTFS 的逆变换：

$$
x(n T_s)
= \frac{1}{N} \sum_{k = 0}^{N - 1} X_k \mathrm{e}^{j \frac{2 \pi n k}{N}}
$$

将 DTFS 中的 $T_s$ 置为 $1$ ，便得到 DFT ：

$$
X[k]
= \sum_{n = 0}^{N - 1} x[n] \mathrm{e}^{-j \frac{2 \pi n k}{N}}
= \sum_{n = 0}^{N - 1} x[n] W^{- n k}
$$

$$
x[n]
= \frac{1}{N} \sum_{k = 0}^{N - 1} X[k] \mathrm{e}^{j \frac{2 \pi n k}{N}}
= \frac{1}{N} \sum_{k = 0}^{N - 1} X[k] W^{n k}
$$

接上节讨论，在上述定义下，若采样足够密、足够多，则在无混叠域内：

$$
\begin{align*}
    X[k]
    &= \sum_{n = 0}^{N - 1} x[n] \mathrm{e}^{-j \frac{2\pi nk}{N}} \\
    &= \sum_{n = 0}^{N - 1} f_1(n T_s) \mathrm{e}^{-j \frac{2\pi nk}{N}} \\
    &= \frac{1}{T_s} \sum_{n = 0}^{N - 1} f_1(n T_s) \mathrm{e}^{-j \frac{2\pi nk}{N}} T_s \\
    &\approx \frac{1}{T_s} \int_{-\infty}^\infty f_1(t) \mathrm{e}^{- j \frac{2 \pi k}{N T_s} t} \mathrm{d} t \\
    &= \frac{1}{T_s} \, F_1 (\omega = \tfrac{2 \pi k}{N T_s} )
\end{align*}
$$

即：

$$
F_1 (\omega = \tfrac{2 \pi k}{N T_s} )
\approx T_s X[k]
$$

说明 $X[k]$ 在足够的条件下可以很好的反映加窗信号 $f_1(t)$ 的频谱。

> 圆卷积的定义也是基于周期延拓的`另：视作圆环路上的循环往复也是可以的`。将两个等长序列进行周期延拓后进行线卷积，所得到的结果就是圆卷积（与原序列等长）的周期延拓。由此，卷积性质在 DFT 表示如下：
>
> $$
y[n] = x[n] \otimes h[n]
\Leftrightarrow
Y[k] = X[k] H[k]
> $$
>
> $$
y[n] = x[n] h[n]
\Leftrightarrow
Y[k] = \frac{1}{N} X[k] \otimes H[k]
> $$
>
> 如果两个序列不等长，需要先对更短的序列补零。另外，若将两序列都补零到与两者线卷积序列长度相同，则圆卷积与线卷积结果相同。利用卷积性质，就可以使用 FFT 快速计算线卷积。

## 7 FFT

FFT 是利用 DFT 公式指数项的性质简化运算的一种方法。按照 DFT 公式直接计算，需要进行 $N^2$ 次复数乘法与 $N(N - 1)$ 次复数加法运算，成本巨大。但是其中的大部分计算其实都是重复的，可以简并。

目前最常见的算法是库利-图基快速傅里叶变换算法（Cooley–Tukey FFT algorithm）。算法最出名的应用是将序列分治为等长的两个子序列，其原理是：幂次项 $\mathrm{e}^{j \frac{2 \pi n k}{N}}$ 的取值具有对称性（即 $W^{nk + \frac{N}{2}} = - W^{nk}$）。而且如果 $n k, N$ 最大公因数大于 $1$ ，还可约去之。这方便我们进一步分而治之，节省计算成本。

此算法应用有两种分治思路。第一种是时域抽取（Cooley-Tukey 蝶形运算），即将 DFT 公式中的项目在时域上重新分组：

$$
\begin{align*}
    X[k]
    &= \sum_{n = 0}^{N - 1} x[n] W_N^{- n k} \\
    &= \sum_{r = 0}^{\frac{N}{2} - 1} x[2r] W_N^{- 2 r k} + \sum_{r = 0}^{\frac{N}{2} - 1} x[2r + 1] W_N^{- (2r + 1) k} \\
    &= \boxed{\sum_{r = 0}^{\frac{N}{2} - 1} x[2r] W_{\frac{N}{2}}^{- r k}} + W_N^{- k} \boxed{\sum_{r = 0}^{\frac{N}{2} - 1} x[2r + 1] W_{\frac{N}{2}}^{- r k}} \\
\end{align*}
$$

由此式，我们就能将整条序列拆解为两个子序列的 DFT 与 $N$ 次 $W_N^{- k}$ 的计算，而子序列又可以进一步拆解。这样整个序列 DFT 的时间复杂度 $T(N)$ 满足：

$$
T(N) = 2 T \left( \frac{N}{2} \right) + O(N)
$$

由[主定理](https://zh.wikipedia.org/wiki/%E4%B8%BB%E5%AE%9A%E7%90%86)就可以得到算法的时间复杂度为 $O(N \log N)$ 。相比改造前更加省时。这种分治的输入顺序是比特反转排列（bit-reversed order），输出依序排列。

第二种分治思路是频域抽取（Gentleman-Sande 蝶形运算），即将 DFT 公式中的项目在频域上重新分组。对 $X[k]$ 的奇数项、偶数项，分别有：

$$
\begin{align*}
    X[2r]
    &= \sum_{n = 0}^{N - 1} x[n] W_N^{- n (2r)} \\
    &= \sum_{n = 0}^{\frac{N}{2} - 1} x[n] W_N^{- n (2r)} + \sum_{n = \frac{N}{2}}^{N - 1} x[n] W_N^{- n (2r)} \\
    &= \sum_{n = 0}^{\frac{N}{2} - 1} x[n] W_N^{- n (2r)} + W_N^{- N r} \sum_{n = 0}^{\frac{N}{2} - 1} x[n + \tfrac{N}{2}] W_N^{- n (2r)} \\
    &= \sum_{n = 0}^{\frac{N}{2} - 1} \{ x[n] + x[n + \tfrac{N}{2}] \} W_{\frac{N}{2}}^{- n r} \\
\end{align*}
$$

$$
\begin{align*}
    X[2r + 1]
    &= \sum_{n = 0}^{N - 1} x[n] W_N^{- n (2r + 1)} \\
    &= \sum_{n = 0}^{\frac{N}{2} - 1} x[n] W_N^{- n (2r + 1)} + \sum_{n = \frac{N}{2}}^{N - 1} x[n] W_N^{- n (2r + 1)} \\
    &= \sum_{n = 0}^{\frac{N}{2} - 1} x[n] W_N^{- n (2r + 1)} + W_N^{- \frac{N}{2} (2r + 1)} \sum_{n = 0}^{\frac{N}{2} - 1} x[n + \tfrac{N}{2}] W_N^{- n (2r + 1)} \\
    &= \sum_{n = 0}^{\frac{N}{2} - 1} \{ x[n] - x[n + \tfrac{N}{2}] \} W_N^{- n (2r + 1)} \\
    &= \sum_{n = 0}^{\frac{N}{2} - 1} \{ x[n] - x[n + \tfrac{N}{2}] \} W_N^{- n} \cdot W_{\frac{N}{2}}^{- n r}
\end{align*}
$$

同样可以将整条序列拆解为两个子序列的 DFT 与 $N$ 次 $W_N^{- k}$ 的计算，而子序列又可以进一步拆解。此算法的时间复杂度也是 $O(N \log N)$ 。这种分治的输出顺序是比特反转排列（bit-reversed order），输入依序排列。

Cooley–Tukey FFT algorithm 的分治能力不局限于2的幂次。只要序列长度 $N$ 能表示成两个整数 $N_1, N_2$ 的乘积，就能将其分解成两个长分别为 $N_1, N_2$ 的 DFT 项目。此部分详细介绍见[此链接](https://zh.wikipedia.org/wiki/%E5%BA%93%E5%88%A9-%E5%9B%BE%E5%9F%BA%E5%BF%AB%E9%80%9F%E5%82%85%E9%87%8C%E5%8F%B6%E5%8F%98%E6%8D%A2%E7%AE%97%E6%B3%95#%E4%B8%80%E8%88%AC%E6%80%A7%E5%88%86%E8%A7%A3[4])。

除了 Cooley–Tukey FFT algorithm ，DFT 还有[其他快速算法](https://zh.wikipedia.org/wiki/%E5%BF%AB%E9%80%9F%E5%82%85%E9%87%8C%E5%8F%B6%E5%8F%98%E6%8D%A2#%E5%85%B6%E4%BB%96%E7%AE%97%E6%B3%95)。

## 8 小结

信号与系统的这些变换之间的关系可以归结为三种基本操作：指数加权 `将频域拓展到复数域` 、周期延拓 `使连续频谱离散化` 、时域采样 `使频谱周期延拓` 。取极限将 FS 推向 FT ，指数加权将 FT 拓展到 LT ，而时域离散化又分别由 LT / FT / FS 引出 ZT / DTFT / DFS 。在离散序列有限长的条件下，频域操作最终以 DFT 的形式在计算机中进行。FFT 则不改变 DFT 本身，只是更高效地完成运算。

面对这些变换，断不能孤立地背诵公式。我们需要关注三个问题：信号在时域中是连续还是离散的、是有限还是无限的、是周期还是非周期的，再结合变换的收敛域与实际采样条件，公式的形式、频谱的形态以及可能出现的误差，便都能顺着这张关系网自然得到。

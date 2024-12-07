# 随机变量

有时我们需要深入系统地探究随机事件的各类性质，将每个采样映射成实数有利于从数学角度分析概率模型。这样的映射（往往是双射）$X: \Omega \to \mathbb{R}$称作**随机变量**（random variable）。实际应用中，$X(\omega)$往往被简写为$X$以强化其作为“数”的属性。为更好描述随机变量的分布情况，我们需要一个**分布函数**（distribution function）$F: \mathbb{R} \to [0, 1]$来表述某变量$X$的值不超过某个数$x \in \mathbb{R}$的概率：
$$F(x) = P(A(x)) = P(\{\omega \in \Omega: X(\omega) \leq x\})$$
> 注：为什么采用“不超过”而不是“等于”，因为在一些概率空间中这样的事件可能是“零测集”，即非空但概率测度为0的集合（参考几何概型），此时讨论这样的分布函数没有意义。

注意到，$P$是对事件的概率测度，也就是说$A(x) = \{\omega \in \Omega: X(\omega) \leq x\}$必须是一个事件（即$A(x) \in \mathcal{F}$）。同时，我们需要引入一个适用于实数集$\mathbb{R}$的概率测度来形式化定义随机变量（显然，在$2^\mathbb{R}$上定义测度不现实）：

> [!TIP|label:Borel集]
> Borel $\sigma$域$\mathcal{B}(\mathbb{R})$是包含$\mathbb{R}$上所有区间$(a, b]$的唯一最小$\sigma$域。其元素称为Borel集。

> 注：$\mathcal{B}(\mathbb{R})$的定义在不同教材上略有偏差，但都保证了其包含实数集上所有点和区间。

> [!TIP|label:F可测和随机变量]
> 对于函数$X: \Omega \to \mathbb{R}$，若给定任一Borel集$B \in \mathcal{B}(\mathbb{R})$，有:
> $$\{X \in B\} = X^{-1}(B) = \{\omega \in \Omega: X(\omega) \in B\} \in \mathcal{F}$$
> 则称$X$是$\mathcal{F}$可测的。若$(\Omega, \mathcal{F}, P)$是概率空间，则该$\mathcal{F}$可测的函数$X$称为随机变量。

> 注：如何快速理解$\mathcal{F}$可测这个概念？牢记：$\mathcal{F}$能够描述场景下所有事件，能用$\mathcal{F}$度量的对象自然也必须是事件。若某个$\{X \in B\}$不是一个事件，那么它就不是$\mathcal{F}$可测的。（提示：掷两个硬币但只能看到第一个的结果，此时什么样的集合不能称为事件？）

随机变量$X$很自然地提供了一个$\mathcal{B}(\mathbb{R})$上的概率测度：
$$P_X(B) := P(\{X \in B\}) = P(X^{-1}(B)) = P(\{\omega \in \Omega: X(\omega) \in B\})$$
本质上，$P_X$是函数$P$和$X^{-1}$的复合。同时，我们扩展上一节中$\sigma(\cdot)$的定义来表示**随机变量生成的$\sigma$域**（即使得$X$可测的最小$\sigma$域）：
$$\sigma(X) = \{X^{-1}(B): B \in \mathcal{B}(\mathbb{R})\}$$

我们可以在此基础上利用特殊的Borel集$(-\infty, x]$定义**累积分布函数**（cumulative distribution function, CDF）：

> [!TIP|label:累积分布函数]
> 随机变量$X$的累积分布函数$F_X: \mathbb{R} \to [0, 1]$定义如下：
> $$F_X(x) = P(X \leq x) = P(\{\omega \in \Omega: X(\omega) \leq x\}) = P_X((-\infty, x])$$

随机变量根据其性质分为以下两类：

> [!TIP|label:离散随机变量]
> 若对于任一$B \in \mathcal{B}(\mathbb{R})$，存在至多可数个不同的实数$x_1, x_2, \dots$满足：
> $$P(X \in B) = \sum_{x_i \in B}P(X = x_i)$$
> 称随机变量$X$为离散随机变量。

对离散随机变量，集合$D = \{x \in \mathbb{R}: P(X = x) \neq 0\}$至多可数且 $\sum_{x \in D} P(X = x) = 1$。其**概率质量函数**（probability density function, PMF）定义为：
$$p_X(x) = P(X = x)$$

> [!TIP|label:连续随机变量]
> 若对于任一$B \in \mathcal{B}(\mathbb{R})$，存在可积函数$f_X: \mathbb{R} \to \mathbb{R}$满足：
> $$P(X \in B) = P_X(B) = \int_Bf_X(x)\mathrm{d}x = \int_\mathbb{R} \mathbf{1}_B(x)f_X(x)\mathrm{d}x$$
> 称随机变量$X$为连续随机变量。

函数$\mathbf{1}_B(\cdot)$定义为：
$$\mathbf{1}_B(x) = \begin{cases}1,& x \in B\\0,& x \notin B\end{cases}$$
函数$f_X$称为**概率密度函数**（probability density function, PDF），其性质如下：
- $f_X$几乎处处非负
- $\int_\mathbb{R} f_X(x)\mathrm{d}x = 1$
- 对任意$\{a\} \in \mathcal{B}(\mathbb{R})$，有$P(X = a) = P_X(\{a\}) = \int_{\{a\}}f_X(x)\mathrm{d}x = 0$（但其逆命题不一定成立）；一般地，$X$是连续随机变量的充要条件是任意可数集的概率测度为0
- $f_X(x) = \frac{\mathrm{d}}{\mathrm{d}x}F_X(x)$

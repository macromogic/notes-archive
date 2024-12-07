# 随机变量的函数

> [!TIP|label:期望（expectation）]
> 若随机变量$X$可积（即$\int_\Omega |X|\mathrm{d}P < \infty$），其数学期望（简称期望）为：
> $$E(X) = \int_\Omega X\mathrm{d}P = \int_\mathbb{R}x\mathrm{d}P_X = \begin{cases}\sum_{x_i} x_ip_X(x_i),& \text{discrete r.v.} \\ \int_{-\infty}^{\infty}xf_X(x)\mathrm{d}x,& \text{continuous r.v.}\end{cases}$$

> 注1：期望存在的前提条件是$X$可积。换言之，期望一定是一有穷值。

> 注2：如何理解$\int_\Omega X\mathrm{d}P$这个积分式？它的完整形式应该是$\int_\Omega X(\omega)\mathrm{d}P(\{\omega\})$，简化成离散求和形式就是$\sum_\Omega X(\omega)P(\{\omega\})$，即每个采样对应的随机变量的值的加权平均，权重为采样对应的概率测度。

现有一（双射）函数$g: \mathbb{R} \to \mathbb{R}$，复合函数$g \circ X$同样也是样本空间到实数的映射。令$Y = g \circ X = g(X)$，$Y$是随机变量的前提条件是对任一$B \in \mathcal{B}(\mathbb{R})$满足：
$$g^{-1}(B) \in \mathcal{B}(\mathbb{R}) \implies X^{-1}(g^{-1}(B)) \in \mathcal{F}$$
即，若原像$g^{-1}(B)$是一个Borel集，其一定对应一个事件。

若$g(X)$为一随机变量且期望存在，则：
$$E(g(X)) = \int_\Omega g(X)\mathrm{d}P = \int_\mathbb{R}g(x)\mathrm{d}P_X = \begin{cases}\sum_{x_i} g(x_i)p_X(x_i),& \text{discrete r.v.} \\ \int_{-\infty}^{\infty}g(x)f_X(x)\mathrm{d}x,& \text{continuous r.v.}\end{cases}$$

> 注：区分函数$g(X)$和期望$E(X)$，前者（可能）是随机变量，而后者是一常量。

> 常见函数的期望：
> - **方差**（variance）：$var(X) = E((X-E(X))^2) = E(X^2) - (E(X))^2$
> - **$k$阶矩**（$k$-th moment）：$E(X^k)$
> - **$k$阶中心矩**（$k$-th central moment）：$E((X-E(X))^k)$

现实中，同一样本空间$\Omega$上可能存在不同的随机变量$X, Y$，其取值来自不同的事件空间$\sigma(X), \sigma(Y)$。由于$X$和$Y$都$\mathcal{F}$可测，我们可以衡量两个事件同时发生的概率：
$$P_{XY}(A, B) = P(\{X \in A\} \cap \{Y \in B\}) = P(\{\omega \in \Omega: X \in A, Y \in B\})$$
回顾独立事件的定义，我们可以类比定义随机变量的独立性：

> [!TIP|label:独立随机变量]
> 若对任意$A, B \in \mathcal{B}(\mathbb{R})$满足$\{X \in A\}$和$\{Y \in B\}$独立，则称随机变量$X$和$Y$独立。

一般地，我们还能定义$\sigma$域的独立性：

> [!TIP|label:独立$\sigma$域]
> 对两个不同的$\sigma$域$\mathcal{G}, \mathcal{H} \subseteq \mathcal{F}$，若任意$A \in \mathcal{G}$和$B \in \mathcal{H}$独立，称$\mathcal{G}$和$\mathcal{H}$独立。

由上述定义可知，随机变量$X$和$Y$独立的充要条件是$\sigma(X)$和$\sigma(Y)$独立，而$X$独立于$\sigma$域$\mathcal{G}$的充分条件是$\sigma(X)$和$\mathcal{G}$独立。

> [!TIP|label:联合累积分布函数（joint CDF）]
> $$F_{XY}(x, y) = P_{XY}((-\infty, x], (-\infty, y]) = P(X \leq x, Y \leq y)$$

$X$和$Y$独立当且仅当$F_{XY}(x, y) = F_X(x)F_Y(y)$。更进一步，若$F_X = F_Y$（或者$P_X = P_Y$），则称$X$和$Y$**独立同分布**（independent identically distributed, i.i.d.）。

> 离散随机变量情形：
> - **联合概率质量函数**（joint PMF）：$p_{XY}(x, y) = P(X = x, Y = y)$
> - **边际分布**（marginal distribution）：$p_X(x) = \sum_{y \in D_Y} p_{XY}(x, y)$
> - 多元函数$Z = g(X, Y)$的PMF（若$Z$是随机变量）：$$p_Z(z) = P(Z = z) = P(\{\omega \in \Omega: g(X(\omega), Y(\omega)) = z\}) = \sum_{(x, y) \in g^{-1}(\{z\})}p_{XY}(x, y)$$
> - $Z$的期望：$$E(Z) = \sum_{z \in D_Z}zp_Z(z) = \sum_{z \in D_Z}\sum_{(x, y) \in g^{-1}(\{z\})}zp_{XY}(x, y) = \sum_{(x, y) \in D_X \times D_Y} g(x, y)p_{XY}(x, y)$$

> 连续随机变量情形：
> - **联合概率密度函数**（joint PDF）：$f_{XY}(x, y)$
> - 边际分布：$f_X(x) = \int_\mathbb{R} p_{XY}(x, y)\mathrm{d}y$
> - $g(X, Y)$的期望（若$g(X, Y)$是随机变量）：$$E(g(X, Y)) = \iint_{\mathbb{R}^2} g(x, y)f_{XY}(x, y)\mathrm{d}x\mathrm{d}y$$

> [!TIP|label:协方差（covariance）和相关系数（correlation）]
> $$cov(X, Y) = E((X-E(X))(Y-E(Y))) = E(XY) - E(X)E(Y)$$
> $$\rho(X, Y) = E\left(\frac{E(X-E(X))}{\sqrt{var(X)}}\frac{E(Y-E(Y))}{\sqrt{var(Y)}}\right) = \frac{cov(X, Y)}{\sqrt{var(X)var(Y)}}$$

随机变量和$X$和$Y$**不相关**（uncorrelated）当且仅当$cov(X, Y) = 0$（或$\rho(X, Y) = 0$）。

> 注：独立随机变量一定不相关，但不相关随机变量不一定独立。

> [!TIP|label:期望和方差的性质]
> - 线性性：$E(aX+bY) = aE(X)+bE(Y)$
> - 积性：若$X$和$Y$独立，则$E(g(X)h(Y)) = E(g(X))E(h(Y))$
> - $var(aX) = a^2var(X)$
> - 若$X$和$Y$不相关，则$var(X+Y) = var(X)+var(Y)$

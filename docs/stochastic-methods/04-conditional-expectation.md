# 条件期望

离散情形：条件PMF
$$p_{Y|X}(y_j|x_i) = \frac{p_{XY}(x_i, y_j)}{p_X(x_i)}$$
> 注：
> $$\begin{align*}P(Y \in B|X\in A) &= \frac{P(X \in A \cap Y \in B)}{P(X \in A)} \\&= \frac{\sum_{x_i \in A}\sum_{y_j \in B}p_{XY}(x_i, y_j)}{\sum_{x_i \in A}p_X(x_i)} \\&\neq \sum_{x_i \in A}\sum_{y_j \in B}p_{Y|X}(y_j|x_i)\end{align*}$$

连续情形：条件PDF
$$f_{Y|X}(y|x) = \frac{f_{XY}(x, y)}{f_X(x)}$$

不失一般性，下文仅讨论离散情形的条件期望。给定$X=x_i$，随机变量$Y$服从该条件下的新概率分布，其PMF可以用$P_{Y|X}(\cdot|X=x_i)$表示，期望$E(Y|X=x_i)$称作$Y$在$X=x_i$条件下的**条件期望**。注意到条件期望$E(Y|X)$是关于随机变量$X$的函数（且也是随机变量）。其性质如下：
- $E(Y|X)$在$\sigma(X)$上也可测
- 对每个$x_i \in D_X$，有$\int_{\{X = x_i\}}E(Y|X)\mathrm{d}P = \int_{\{X = x_i\}}Y\mathrm{d}P$，即$E(E(Y|X)\mathbf{1}_{\{X = x_i\}}) = E(Y\mathbf{1}_{\{X = x_i\}})$
> 注：第二条性质可以理解为，在限定$X$的取值的情况下，随机变量$E(Y|X)$和$Y$的期望相等。

> [!TIP|label:全期望公式]
> $$E(Y) = E(E(Y|X))$$

离散条件期望的其它性质：
- 令$A_1, A_2, \dots$是$\Omega$的一个可数分割，则$E(X) = \sum_{i=1}^\infty E(X|A_i)P(A_i)$
- 若随机变量$Y = h(X)$，则$E(Y|X) = h(X)$
- 若$X, Y$是同一样本空间内两随机变量，且$g(X)$也是随机变量，则$E(g(X)Y|X) = g(X)E(Y|X)$

现在我们拓展到一般情形。
> [!TIP|label:基于事件的条件期望]
> 对任意可积随机变量$X: \Omega \to \mathbb{R}$和事件$B \in \mathcal{F}$，若$P(B) \neq 0$，则$X$在给定事件$B$上的条件期望为：
> $$E(X|B) = \frac{1}{P(B)}\int_BX\mathrm{d}P$$

> [!TIP|label:基于随机变量的条件期望]
> 令$Y: \Omega \to \mathbb{R}$是可积随机变量，$X: \Omega \to \mathbb{R}$是任一随机变量，则$Y$在$X$上的条件期望$E(Y|X)$在$\sigma(X)$上可测，并且对任意$B \in \sigma(X)$：
> $$\int_BE(Y|X)\mathrm{d}P = \int_BY\mathrm{d}P$$

我们可以进一步拓展到子$\sigma$域$\mathcal{G} \subseteq \mathcal{F}$：
> [!TIP|label:基于子σ域的条件期望]
> 令$X: \Omega \to \mathbb{R}$是可积随机变量，$\mathcal{G} \in \mathcal{F}$是一$\sigma$域，则$X$在$\mathcal{G}$上的条件期望$E(X|\mathcal{G})$在$\mathcal{G}$上可测，并且对任意$B \in \mathcal{G}$：
> $$\int_BE(X|\mathcal{G})\mathrm{d}P = \int_BX\mathrm{d}P$$

条件期望的性质：
- 线性性：$E(aX+bY|\mathcal{G}) = aE(X|\mathcal{G}) + bE(Y|\mathcal{G})$
- 若$X$独立于$\mathcal{G}$，则$E(X|\mathcal{G}) = E(X)$
- **塔性质**（tower property，全期望公式的一般形式）：若$\mathcal{H} \subseteq \mathcal{G}$，则$E(E(X | \mathcal{G}) |\mathcal{H}) = E(X | \mathcal{H})$
- 若$X$在$\mathcal{G}$上可测，则$E(X|\mathcal{G}) = X$；一般地，$E(XY|\mathcal{G}) = XE(Y|\mathcal{G})$

# 随机空间

> [!TIP|label:集合论回顾]
> - 有限集合、可数集合（和自然数集$\mathbb{N}$存在一一对应）、不可数集合
> - **幂集**（power set）：集合$A$的所有子集构成的集合，记作$2^A$
> 	- 定义式：$2^A = \{B: B \subseteq A\}$
> 	- 若$A$有限，则$|2^A| = 2^{|A|}$；若$A$可数，则$|2^A| = |A| = \aleph_0$

如何描述一个**事件**（event）？事件是一系列**采样/结果**（sample/outcome）的集合。实验中所有可能的采样的集合称作**样本空间**（sample space），记作$\Omega$。显然任一事件都是$\Omega$的子集或$2^\Omega$的元素。特殊地，$\varnothing$称为**不可能事件**（impossible event），$\Omega$本身称为**必然事件**（certain event）。

> 注：事件的划分和当前能否区分不同采样有关。比如，实验掷了两次硬币但只能看到第一次的结果，那么“正正”和“正反”两个采样在当前情境下无法分辨，因此无法归类到不同事件中。

为更好地描述事件间的关系，我们需要讨论事件的交集（$A \cap B$）、并集（$A \cup B$）、补集（$A^c$）以及差集（$A \setminus B = A \cap B^c$）。如果某个事件集合$\mathcal{F} \subseteq 2^\Omega$对于上述运算不封闭（即，集合内一些元素运算结果不在这个集合内），则讨论没有意义。我们引入以下定义来形式化描述**事件空间**（event space）：

> [!TIP|label:σ域]
> 集合$\mathcal{F} \subseteq 2^\Omega$被称作$\sigma$域当且仅当$\mathcal{F}$满足下列三个条件：
> - $\varnothing \in \mathcal{F}$（包含空元素，后续的概率测度需要这个条件）
> - 若$A \in \mathcal{F}$，则$A^c \in \mathcal{F}$（对补集封闭）
> - 若至多可数个集合列$A_1, A_2, \dots \in \mathcal{F}$，则$\bigcup_{i=1}^\infty A_i \in \mathcal{F}$（对可数并集封闭）

不难证明，$\sigma$域对交集和差集运算也封闭。同时，两$\sigma$域的交集也是$\sigma$域（但并集不是）。对任一事件集合$\mathcal{F}$，存在**唯一最小**的包含$\mathcal{F}$的$\sigma$域，记作$\sigma(\mathcal{F})$。

在描述不同事件的概率时，显然需要遵循以下规则：
- 任意事件的概率在区间$[0, 1]$内
- $\varnothing$的概率为0，$\Omega$的概率为1
- 若至多可数个事件互斥（即任意交集为$\varnothing$），其并集的概率等于各自概率之和

也就是说，概率函数满足**测度**（measure）的定义（非负、空集测度为0、可数可加性），形式化描述如下：

> [!TIP|label:概率测度（probability measure）]
> 令$\Omega$为样本空间，$\mathcal{F} \subseteq 2^\Omega$是$\Omega$上一个$\sigma$域，函数$P: \mathcal{F} \to [0, 1]$为$(\Omega, \mathcal{F})$上的概率测度当且仅当其满足下列条件：
> - $P(\varnothing) = 0, P(\Omega) = 1$
> - 若至多可数个集合列$A_1, A_2, \dots \in \mathcal{F}$满足$\forall i, j: A_i \cap A_j = \varnothing$，则$P(\bigcup_{i=1}^\infty A_i) = \sum_{i=1}^\infty P(A_i)$

> [!TIP|label:概率空间（probability space）]
> 若$\mathcal{F} \subseteq 2^\Omega$是$\Omega$上的$\sigma$域且$P$是$(\Omega, \mathcal{F})$上的概率测度，则三元组$(\Omega, \mathcal{F}, P)$是一个概率空间。

> 注：上文提到了事件的划分，“无法再细分”（即无法区分其中的采样）的事件被称为**原子**（atom）。其充要条件为：$P(A) > 0$且$\forall B \subseteq A: P(B) < P(A) \implies P(B) = 0$。在事件空间较大不易枚举时，可考虑枚举其中的原子。

> [!TIP|label:条件概率（conditional probability）]
> 在事件$B$发生的条件下，事件$A$发生的概率称为条件概率：
> $$P(A|B) = \frac{P(A \cap B)}{P(B)}$$
> $P(A)$称为事件$A$的**先验概率**（prior probability），而$P(A|B)$称为$A$在$B$条件下的**后验概率**（posterior probability）。

> [!TIP|label:全概率定律（law of total probability）]
> 令$A_1, A_2, \dots, A_n$是$\Omega$的一个分割（即，$\Omega$是$A_1, A_2, \dots, A_n$的不交并）且$A_i \in \mathcal{F}$，对任意$B \in \mathcal{F}$，有：
> $$P(B) = \sum_{i=1}^nP(B|A_i)P(A_i)$$

> [!TIP|label:贝叶斯公式]
> $$P(A_i|B) = \frac{P(B|A_i)P(A_i)}{\sum_{j=1}^nP(B|A_j)P(A_j)}$$
> 或
> $$P(A|B) = \frac{P(B|A)P(A)}{P(B|A)P(A)+P(B|A^c)P(A^c)}$$

> [!TIP|label:独立事件]
> 若$P(A\cap B) = P(A)P(B)$，我们称事件$A$和$B$独立。

> 注：多个事件的场景下，两两（pairwise）独立和相互（mutually）独立不等价。

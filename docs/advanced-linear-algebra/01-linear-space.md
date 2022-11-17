# 线性空间和线性映射

若一个集合$V$装备了以下两种运算：
- *加法* $+: V \times V \to V: (x, y) \to x+y$
- *常数乘法* $\cdot: \mathbb{F} \times V \to V: (a, x) \to ax$

且运算满足以下性质：
- $x+y = y+x$
- $x+(y+z) = (x+y)+z$
- 存在$\mathbf{0}$使得$\mathbf{0}+x = x$
- $1 \cdot x = x$
- $(a_1a_2)x = a_1(a_2x)$
- $a(x+y) = ax + ay$
- $(a_1+a_2)x = a_1x + a_2x$

我们称$V$是一个$\mathbb{F}$上的**线性空间**。

---

令$V, W$是线性空间，$\varphi$是一个从$V$到$W$的映射，若下述条件成立：
- $\varphi(x+y) = \varphi(x) + \varphi(y)$
- $\varphi(ax) = a\varphi(x)$

则称$\varphi$是一个**线性映射**。

特殊地，若$\varphi$是一个双射，称$V$和$W$**同构**，记作$V \simeq W$。

---

为了表示一个线性空间，我们可以尝试寻找一个*最小*的元素集合$\{x_1, x_2, \dots, x_n\}$使得任意元素都能用该集合的元素以及“$+$”和“$\cdot$”这两个运算符表示。

对于一系列向量$x_1, x_2, \dots, x_n$，形如$\sum_{i=1}^n c_ix_i$的式子称为这些向量的**线性组合**。
若空间$V$中所有元素都能写成$x_1, x_2, \dots, x_n$的线性组合，我们称这些向量**张成**整个空间$V$，记作$V = \operatorname{span}\{x_1, \dots, x_n\} = \{\sum_{i=1}^n c_ix_i : c_i \in \mathbb{F}\}$。

若存在非零的$c_1, c_2, \dots, c_n$使得$\sum_{i=1}^n c_ix_i = 0$，则$x_1, x_2, \dots, x_n$**线性相关**。否则这些向量**线性无关**。

注：若$x_1, x_2, \dots, x_n$线性相关，不妨设$c_i \neq 0$，由$\sum_{i=1}^n c_ix_i = 0$可以得到$x_i = \sum_{j \neq i} -\frac{c_j}{c_i}x_j$，因此$x_1, x_2, \dots, x_n$的线性组合可以由$x_1, x_2, \dots, x_{i-1}, x_{i+1}, \dots, x_n$的线性组合表示。

---

令$X$是一个线性空间，$Y \subseteq X$，若*加法*和*常数乘法*在$Y$上封闭，则$Y$是$X$的一个**子空间**。

令$Y, Z \subseteq X$，若$Y, Z$都是$X$的子空间，则$Y+Z = \{y+z : y \in Y, z \in Z\}$也是$X$的子空间。

**引理** 若$V$由$x_1, \dots, x_n$张成，$y_1, \dots, y_j \in V$线性无关，则$j \leq n$。
> **证明**  \
> 用$x_1, \dots, x_n$的线性组合来表示$y_1 = \sum_{i=1}^n c_ix_i$，对于某个（系数非零的）$x_i$，可以将它写成$x_i = \frac{1}{c_i}y_1 + \sum_{k \neq i} -\frac{c_k}{c_i}x_k$。用$y_1$代替$x_i$，此时$x_1, \dots, x_{i-1}, y_1, x_{i+1}, \dots, x_n$依然张成$V$。\
> 由上述知，$y_2$可以写成$x_1, \dots, x_{i-1}, x_{i+1}, \dots, x_n$的线性组合（这里不包含$y_1$项是因为$y_1, \dots, y_j$线性无关）。同理可以找到一个$x_i'$并替换。\
> 重复该过程，若$j > n$，最终$V = \operatorname{span}\{x_1, \dots, x_n\} = \operatorname{span}\{y_1, \dots, y_n\} \subseteq \operatorname{span}\{y_1, \dots, y_j\}$，而根据题意，$\operatorname{span}\{y_1, \dots, y_j\} \subseteq V = \operatorname{span}\{y_1, \dots, y_n\}$，所以有$\operatorname{span}\{y_1, \dots, y_j\} = \operatorname{span}\{y_1, \dots, y_n\}$，与假设矛盾。\
> 因此$j \leq n$。QED

---

令$V$是线性空间，若$x_1, \dots, x_n$线性无关且张成$V$，则这些向量是$V$的一组**基底/基**。

**引理** 若$V$可以由有限个向量张成，则$V$有一组基底。（删去线性相关的部分即可）

若线性空间$V$有一组基底，我们称$V$是**有限维**的。

**定理** 令$V$是有限维线性空间，若$\{y_1, \dots, y_m\}$是其中线性无关的子集，该集合可以被扩充为一组基底。（不在该集合张成的空间里的向量必然和集合内向量线性无关，因此可以进行扩充）
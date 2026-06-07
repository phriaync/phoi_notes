# 莫比乌斯反演

## 莫比乌斯函数
$$
\mu(n) = \begin{cases}
1 & n = 1 \newline
0 & \exists a \geq 2, a \in \mathbb{N}, a^2 \mid n \newline
(-1)^k & n = \prod_{i = 1}^k p_i, p_i \in \text{Prime}
\end{cases} 
$$
显然莫比乌斯函数为积性函数，但不为完全积性函数。

同时，莫比乌斯函数具有重要性质：
$$
\sum_{d \mid n}\mu(d) = [n = 1]
$$

??? note "证明"
    当 $n = 1$ 时，$\sum_{d \mid n}\mu(d) = 1$。

    否则，设 $n = \prod_{i = 1}^k p_i^{a_i},m = \prod_{i = 1}^k p_i$，此时：
    $$
    \begin{aligned}
    \sum_{d \mid n}\mu(d) 
    &= \sum_{d \mid m}\mu(d) \newline
    &= \sum_{i = 0}^k \dbinom{k}{i}(-1)^i \newline
    &= (1 - 1)^k \newline
    &= 0
    \end{aligned}
    $$

    故 $\sum_{d \mid n}\mu(d) = [n = 1]$。

应用该性质可以得到：
$$
[i \perp j] = \sum_d [d \mid i][d \mid j]\mu(d)
$$

??? note "证明"
    \$
    \begin{aligned}
    [i \perp j]
    &= [\gcd(i, j) = 1] \newline
    &= \sum_{d \mid \gcd(i, j)}\mu(d) \newline
    &= \sum_d [d \mid i][d \mid j]\mu(d)
    \end{aligned}
    \$
其将两数互素的条件转化为一个求和式，方便进一步推导。

## 莫比乌斯反演
设 $f(n), g(n)$ 为两个数论函数，则：
$$
f(n) = \sum_{d|n}g(d) \iff g(n) = \sum_{d|n}\mu(\frac{n}{d})f(d)
$$

??? note "证明"



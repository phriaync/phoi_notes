# 扩展欧几里得算法（exgcd）
exgcd 能够求出形如 $ax + by = \gcd(a, b)$ 的方程的一组特解。

## 过程 & 原理
对于方程 $ax + by = \gcd(a, b)$，
我们考虑求出方程 $(b \bmod a)x + ay = \gcd(a, b)$ 的一组解，
进而反推出原方程的一组解。

根据辗转相除法，该递归过程的边界情况为 $0x + \gcd(a, b)y = \gcd(a, b)$，此时有：
$$
\begin{cases}
  x \in \mathbb{R} \newline
  y = 1
\end{cases}
$$
符合方程。为方便计算以及防止解过大，通常取 $x = 0$。

又 
$$
\begin{aligned}
  (b \bmod a)x + ay = \gcd(a, b) \newline
  \iff (b - a\lfloor \frac{b}{a} \rfloor )x + ay = \gcd(a, b) \newline
  \iff a(y - \lfloor \frac{b}{a} \rfloor x) + bx = \gcd(a, b)
\end{aligned}
$$
故得到方程 $(b \bmod a)x + ay = \gcd(a, b)$ 的一组解
$x = x_0, y = y_0$ 后，可以得到方程 $ax + by = \gcd(a, b)$ 的一组解：
$$
\begin{cases}
  x = y_0 - \lfloor \frac{b}{a} \rfloor x_0 \newline
  y = x_0
\end{cases}
$$
重复该过程即可得到原方程的一组特解。

## 得到通解
由
$$
\begin{aligned}
  ax + by = \gcd(a, b)
  \iff a(x + btk) + b(y - atk) = \gcd(a, b)
\end{aligned}
$$
得 $k \in \mathbb{Z}$ 时，使 $btk, atk \in \mathbb{Z}$ 的 $t_{min} = \frac{1}{\gcd(a, b)}$，于是原方程有通解式：
$$
\begin{cases}
  x = x_0 + \frac{b}{\gcd(a, b)}k \newline
  y = y_0 - \frac{a}{\gcd(a, b)}k 
\end{cases}
$$
其中 $k \in \mathbb{Z}$。
# 柯西-比内公式的推演(手稿转录)

> 本文按图片序号($1 \to 19$)逐页转录手稿中柯西-比内公式(Cauchy–Binet formula)的推演过程。
> 说明:第 17、18 页内容完全相同(为同一张图的重复),本文合并为「图 17 / 18」一节。
> 全文数学符号遵循标准 LaTeX/TeX 记法(以 `\vert`、`\Vert` 代替 `|`、`||`)。

---

## 图 1 — 记号与置换矩阵的定义

设 $[e_1, e_2, e_3, \ldots, e_k]$ 为 $\mathbb{R}^k$ 上的标准单位基底向量。

- $N_k$ 表示自然数 $1, 2, \ldots, k$。
- $A_k$ 表示 $N_k$ 的全排列(permutation)集合,$\vert A_k \vert = k!$。

对 $\rho = (i_1, i_2, \ldots, i_k) \in A_k$,定义矩阵

$$
R_\rho = [e_{i_1}, e_{i_2}, \ldots, e_{i_k}]
$$

令 $\pi_e = (1, 2, 3, \ldots, k) \in A_k$,$\pi_e$ 可以看成是一个恒等排列。

给定向量 $\alpha = (a_1, a_2, \ldots, a_k)$,则

$$
\alpha R_\rho = [\langle \alpha, e_{i_1}\rangle, \langle \alpha, e_{i_2}\rangle, \ldots, \langle \alpha, e_{i_k}\rangle]
$$

$$
= [a_j \delta_{j i_1}, a_j \delta_{j i_2}, \ldots, a_j \delta_{j i_k}]
$$

$$
= [a_{i_1}, a_{i_2}, \ldots, a_{i_k}]
$$

(上式对下标 $j$ 采用爱因斯坦求和约定,$\delta$ 为克罗内克记号(Kronecker delta)。)

即 $\alpha R_\rho$ 为对 $\alpha$ 的元素按照排列 $\rho$ 进行重排。

---

## 图 2 — 二元运算与列交换矩阵分解

显然 $\pi_e R_\rho = \rho$。

在 $A_k$ 上定义二元运算 $\circ$:$\forall \rho_1, \rho_2 \in A_k$

$$
\rho_1 \circ \rho_2 = \rho_1 R_{\rho_2}
$$

即 $\rho_2$ 作用时对 $\rho_1$ 做重排,因为 $\rho_1 R_{\rho_2} \in A_k$。

$R = [e_{i_1}, e_{i_2}, \ldots, e_{i_k}]$,$R$ 可以看成是列重排矩阵,则 $R$ 可分解为一系列初等的列交换矩阵。用 $E_{(m,n)}$ 表示初等列交换矩阵:

$$
E_{(m,n)} = \begin{cases} I, & m = n \text{(不做交换)} \\[4pt] E_{(m,n)}, & m \neq n \text{(交换矩阵的第 } m \text{ 列和第 } n \text{ 列)} \end{cases}
$$

显然,任意 $R$ 可分解为 $k$ 个交换矩阵的乘积。以下用数学归纳法(mathematical induction)证明。

- $k=1$ 时,$\mathbb{R}^1$ 的标准基为 $e_1$,$R = [1]$,显然 $R = E_{(1,1)}$。
- 假设当 $k=t$ 时,在 $\mathbb{R}^t$ 上有 $R = E_{(1, i_1)} E_{(2, i_2)} \cdots E_{(t, i_t)}$。

---

## 图 3 — 归纳步骤

当 $k = t+1$ 时,$\mathbb{R}^{t+1}$ 上的 $R = (e_{j_1}, e_{j_2}, \ldots, e_{j_t}, e_{j_{t+1}})$。

遍历 $R$ 的列向量,找到

$$
e_{i_q} = \begin{pmatrix} 0 \\ 0 \\ \vdots \\ 1 \end{pmatrix}
$$

用 $E_{(t+1,\, i_q)}$ 交换 $R$ 的第 $t+1$ 列和第 $i_q$ 列:

$$
R\, E_{(t+1,\, i_q)} = \begin{bmatrix} R'_{(t \times t)} & 0_{(t \times 1)} \\[4pt] 0_{(1 \times t)} & 1 \end{bmatrix}
$$

其中 $R'$ 为 $\mathbb{R}^t$ 上的列重排矩阵。

由假设得知 $R' = E_{(1, i_1)} E_{(2, i_2)} \cdots E_{(t, i_t)}$。

显然

$$
R\, E_{(t+1,\, i_q)} = E_{(1, i_1)} E_{(2, i_2)} \cdots E_{(t, i_t)}
$$

$$
R = E_{(1, i_1)} E_{(2, i_2)} \cdots E_{(t, i_t)}\, E_{(t+1,\, j_q)}^{-1}
$$

对于 $E_{(m,n)}$,满足下列性质。

---

## 图 4 — 交换矩阵的性质与重排矩阵集合

$E_{(m,n)}$ 满足:

1. $E_{(m,n)} = E_{(m,n)}^T$(对称性)
2. $E_{(m,n)} = E_{(m,n)}^{-1}$(自逆/对合矩阵)
3. $E_{(m,n)} = E_{(m,n)}$(交换 $m \leftrightarrow n$ 列等价于交换 $n \leftrightarrow m$ 列)

$\forall R$ 可分解为 $R = E_{i_1} E_{i_2} \cdots E_{i_k}$,则

$$
R^{-1} = R^T = (E_{i_1} E_{i_2} \cdots E_{i_k})^T = E_{i_k}^T \cdots E_{i_2}^T E_{i_1}^T = E_{i_k} \cdots E_{i_2} E_{i_1}
$$

即 $R^{-1}, R^T$ 均为重排矩阵。

$R_1$ 和 $R_2$ 为重排矩阵,则 $R_1 R_2$ 也是重排矩阵。

定义 $P(\mathbb{R}^k)$ 为 $\mathbb{R}^k$ 上标准单位基底向量 $(e_1, e_2, \ldots, e_k)$ 构成的所有可能重排矩阵。

---

## 图 5 — $(P(\mathbb{R}^k), \times)$ 构成群

取 $\times$ 为矩阵乘法,则代数系统 $(P(\mathbb{R}^k), \times)$ 为群(group):

1. **封闭性**:$R_1, R_2 \in P(\mathbb{R}^k) \Rightarrow R_1 R_2 \in P(\mathbb{R}^k)$。
2. **单位元**:$I \in P(\mathbb{R}^k)$,$I R_1 = R_1 I = R_1$。
3. **逆元存在**:$R = E_{(1, i_1)} E_{(2, i_2)} \cdots E_{(k, i_k)}$,则

$$
R^{-1} = E_{(k, i_k)} \cdots E_{(2, i_2)} E_{(1, i_1)}, \qquad R R^{-1} = R^{-1} R = I
$$

4. **交换律不满足**:$\exists R_1, R_2 \in P(\mathbb{R}^k)$,使 $R_1 R_2 \neq R_2 R_1$。
5. **结合律满足**:$(R_1 R_2) R_3 = R_1 (R_2 R_3)$,矩阵乘法结合律满足。

定义 $T: A_k \to P(\mathbb{R}^k)$,对 $\rho = (i_1, i_2, \ldots, i_k)$

$$
T(\rho) = [e_{i_1}, e_{i_2}, \ldots, e_{i_k}]
$$

---

## 图 6 — $T$ 为同构映射,$(A_k, \circ)$ 为群

$T$ 为双射(bijection):

1. $\rho_1, \rho_2 \in A_k$,$\rho_1 \neq \rho_2 \Rightarrow T(\rho_1) \neq T(\rho_2)$。
2. $\forall R \in P(\mathbb{R}^k)$,$\exists \rho \in A_k$ 使得 $T(\rho) = R$。

所以 $T$ 存在逆映射 $T^{-1}: P(\mathbb{R}^k) \to A_k$,满足

$$
T^{-1}(T(\rho)) = \rho
$$

$(A_k, \circ)$ 满足 $\forall \rho_1, \rho_2 \in A_k$:

$$
\rho_1 \circ \rho_2 = T^{-1}(T(\rho_1) T(\rho_2))
$$

即 $T(\rho_1 \circ \rho_2) = T(\rho_1) T(\rho_2)$,$T$ 是 $(A_k, \circ)$ 和 $(P(\mathbb{R}^k), \times)$ 的同构映射(isomorphism)。

**单位元**:$\pi_e = T^{-1}(I)$,

$$
\pi_e \circ \rho = T^{-1}(T(\pi_e) T(\rho)) = T^{-1} T(\rho) = \rho
$$

同理 $\rho \circ \pi_e = \rho$。

**逆元存在**:$\forall \rho \in A_k$,考察 $T^{-1}[T(\rho)^{-1}]$,即

$$
\rho \circ T^{-1}[T(\rho)^{-1}]
$$

---

## 图 7 — 逆元与结合律验证

$$
\rho \circ T^{-1}[T(\rho)^{-1}] = T^{-1}\big(T(\rho) \cdot T(T^{-1}[T(\rho)^{-1}])\big)
$$

$$
= T^{-1}\big(T(\rho) \cdot T(\rho)^{-1}\big)
$$

$$
= T^{-1}(I)
$$

$$
= \pi_e
$$

3. **不满足交换律**:略。
4. **满足结合律**:

$$
(\rho_1 \circ \rho_2) \circ \rho_3 = T^{-1}(T(\rho_1 \circ \rho_2) T(\rho_3))
$$

$$
= T^{-1}(T(\rho_1) T(\rho_2) T(\rho_3))
$$

$$
= T^{-1}(T(\rho_1)[T(\rho_2) T(\rho_3)])
$$

$$
= \rho_1 \circ (\rho_2 \circ \rho_3)
$$

**结论**:$(A_k, \circ)$ 是满足结合律的群。

定义 $A_k^2 = A_k \times A_k$。

---

## 图 8 — $\text{span}$ 与划分集 $D$

$$
(\rho_1, \rho_2) \in A_k^2 \iff \rho_1 \in A_k \text{ 且 } \rho_2 \in A_k
$$

定义 $f: A_k^2 \times A_k \to A_k^2$,$f[(\rho_1, \rho_2), \pi] = (\rho_1 \circ \pi, \rho_2 \circ \pi)$。

$$
\text{span}(\rho_1, \rho_2) = \{(\rho_1 \circ \pi, \rho_2 \circ \pi) \mid \pi \in A_k\}
$$

$$
\vert \text{span}(\rho_1, \rho_2) \vert = \vert A_k \vert = k!
$$

令 $D = \{(\pi_e, \rho) \mid \rho \in A_k\}$,显然

$$
D \subseteq A_k^2, \qquad \vert D \vert = \vert A_k \vert = k!
$$

$d_1, d_2 \in D$ 且 $d_1 \neq d_2 \iff \text{span}(d_1) \neq \text{span}(d_2)$。

**求证**:$\text{span}(d_1) \neq \text{span}(d_2) \iff \text{span}(d_1) \cap \text{span}(d_2) = \emptyset$。

使用反证法。若 $d \in \text{span}(d_1) \cap \text{span}(d_2)$,设

$$
d_1 = (\pi_e, \rho_1), \qquad d_2 = (\pi_e, \rho_2)
$$

$$
d_1 \neq d_2 \iff \rho_1 \neq \rho_2
$$

令 $d = (\rho_3, \rho_4)$,则存在 $\rho', \rho''$ 使得

$$
(\pi_e, \rho_1) \circ \rho' = (\rho_3, \rho_4)
$$

$$
(\pi_e, \rho_2) \circ \rho'' = (\rho_3, \rho_4)
$$

---

## 图 9 — 反证法推导矛盾

分量展开:

$$
\pi_e \circ \rho' = \rho_3 \quad \text{①}
$$

$$
\rho_1 \circ \rho' = \rho_4 \quad \text{②}
$$

$$
\pi_e \circ \rho'' = \rho_3 \quad \text{③}
$$

$$
\rho_2 \circ \rho'' = \rho_4 \quad \text{④}
$$

由 ①③ $\Rightarrow \rho' = \rho'' = \rho_3 \quad$ ⑤

将 ⑤ 代入 ②④:

$$
\rho_1 \circ \rho_3 = \rho_4 \quad \text{⑥}
$$

$$
\rho_2 \circ \rho_3 = \rho_4 \quad \text{⑦}
$$

由 ⑥⑦:

$$
\rho_1 = \rho_1 \circ \rho_3 \circ \rho_3^{-1} = \rho_4 \circ \rho_3^{-1}
$$

$$
\rho_2 = \rho_2 \circ \rho_3 \circ \rho_3^{-1} = \rho_4 \circ \rho_3^{-1}
$$

得出 $\rho_1 = \rho_2 = \rho_4 \circ \rho_3^{-1}$,与 $\rho_1 \neq \rho_2$ 矛盾。因此:

$$
\forall d_1, d_2 \in D, \quad d_1 \neq d_2 \iff \text{span}(d_1) \cap \text{span}(d_2) = \emptyset
$$

又 $\vert \text{span}(d) \vert = k!$,故

$$
\left\vert \bigcup_{d \in D} \text{span}(d) \right\vert = \sum_{d \in D} \vert \text{span}(d) \vert = (k!)^2
$$

---

## 图 10 — $\text{span}(d)$ 的符号性质

因 $\vert A_k^2 \vert = (k!)^2$,故

$$
A_k^2 / D = \{\text{span}(d) \mid d \in D\}
$$

是对 $A_k^2$ 的一个划分。研究 $\text{span}(d)$ 的性质。

**求证** $\forall d_1 = (\rho_1, \rho_2) \in \text{span}(d)$,令

$$
\text{sgn}(d_1) = \text{sgn}(\rho_1)\,\text{sgn}(\rho_2) = \det(T(\rho_1))\det(T(\rho_2)) = \det(T(\rho_1)T(\rho_2))
$$

设生成元为 $(\pi_e, \pi)$,则 $d_1 = (\rho_1, \rho_2) = (\pi_e \circ \rho_1,\; \pi \circ \rho_1)$,于是

$$
\text{sgn}(d_1) = \det\big(T(\pi_e \circ \rho_1)\, T(\pi \circ \rho_1)\big)
$$

$$
= \det\big(T(\pi_e)\, T(\rho_1)\, T(\pi)\, T(\rho_1)\big)
$$

$$
= \det(T(\pi_e))\, \det(T(\pi))\, \det(T(\rho_1))^2
$$

因为 $\det(T(\rho_1))^2 = 1$,$\det(T(\pi_e)) = \det(I) = 1$,所以

$$
\text{sgn}(d_1) = \det(T(\pi_e))\, \det(T(\pi)) = \text{sgn}(\pi)
$$

即 $\forall (\rho_1, \rho_2) \in \text{span}(\pi_e, \pi)$:

$$
\text{sgn}(\rho_1, \rho_2) = \text{sgn}(\rho_1) \cdot \text{sgn}(\rho_2) = \text{sgn}(\pi)
$$

---

## 图 11 — 引理(划分 $A_k^2 / A_k$ 的性质)

$$
A_k^2 / A_k = \{\text{span}(\pi_e, \pi) \mid \pi \in A_k\}
$$

是 $A_k^2$ 的一个划分,满足:

1. $\vert A_k^2 / A_k \vert = k!$
2. $\vert \text{span}(\pi_e, \pi) \vert = k!$
3. $\vert A_k^2 \vert = (k!)^2$
4. $\text{span}(\rho_1, \rho_2) = \text{span}(\pi_e,\; \rho_2 \circ \rho_1^{-1})$
5. $\text{sgn}(\rho_1, \rho_2) = \text{sgn}(\rho_1) \cdot \text{sgn}(\rho_2) = \text{sgn}(\rho_2 \circ \rho_1^{-1})$
6. $\forall (\rho_1, \rho_2) \in \text{span}(\pi_e, \pi)$,$\text{sgn}(\rho_1) \cdot \text{sgn}(\rho_2) = \text{sgn}(\pi)$
7. (下续)

---

## 图 12 — 柯西-比内公式的表述

**证明 $k$ 阶柯西-比内公式(Cauchy–Binet formula)。**

令 $M_1 = (a_{ij})_{n \times k}$,$M_2 = (b_{ij})_{n \times k}$,即 $M_1, M_2$ 为 $\mathbb{R}$ 上的 $n \times k$ 矩阵。

令 $p \in N_n^k$,$p = (p_1, p_2, \ldots, p_k)$。$M_1[p]$、$M_2[p]$ 表示选 $M_1, M_2$ 的第 $p_1, p_2, \ldots, p_k$ 行构成的 $k \times k$ 方阵,即

$$
M_1[p] = (a_{p_i j})_{k \times k}, \qquad M_2[p] = (b_{p_i j})_{k \times k}
$$

> **柯西-比内公式表述为**
>
> $$\det(M_1^T M_2) = \sum_p \det(M_1[p]) \det(M_2[p])$$
>
> 且 $p \in A_k$,$p = (p_1, p_2, \ldots, p_k)$ 且 $p_i < p_{i+1}$,$i = 1, 2, \ldots, k-1$。

在柯西-比内公式中 $p$ 是 $1, 2, \ldots, n$ 中的一个组合。我们将非平凡项 $p \in N_n^k$ 都考虑进去。

---

## 图 13 — 定义 $H$ 并展开

定义

$$
H = \sum_{p \in N_n^k} \det(M_1[p]) \det(M_2[p])
$$

令 $H(p) = \det(M_1[p]) \det(M_2[p])$,显然

$$
H = \sum_{p \in N_n^k} H(p)
$$

将每个 $k \times k$ 行列式按排列展开:

$$
H(p) = \left(\sum_{\pi_1 \in A_k} \text{sgn}(\pi_1) \prod_{s=1}^{k} a[p_s, i_s]\right) \cdot \left(\sum_{\pi_2 \in A_k} \text{sgn}(\pi_2) \prod_{t=1}^{k} b[p_t, j_t]\right)
$$

其中 $(\pi_1, \pi_2) \in A_k^2$ 且 $\pi_1 = (i_1, i_2, \ldots, i_k)$,$\pi_2 = (j_1, j_2, \ldots, j_k)$。

(为避免 typo,用 $a[p_s, i_s]$、$b[p_t, j_t]$ 代替 $a_{p_s i_s}$、$b_{p_t j_t}$。)

令

$$
H(p, \pi_1, \pi_2) = \text{sgn}(\pi_1)\,\text{sgn}(\pi_2) \prod_{s=1}^{k} a[p_s, i_s] \prod_{t=1}^{k} b[p_t, j_t]
$$

$$
= \text{sgn}(\pi_1)\,\text{sgn}(\pi_2) \prod_{s=1}^{k} a[p_s, i_s]\, b[p_s, j_s]
$$

显然

$$
H(p) = \sum_{(\pi_1, \pi_2) \in A_k^2} H(p, \pi_1, \pi_2)
$$

$$
H = \sum_{p \in N_n^k} H(p) = \sum_{p \in N_n^k} \; \sum_{(\pi_1, \pi_2) \in A_k^2} H(p, \pi_1, \pi_2)
$$

令 $C_{k \times k} = M_1^T M_2$,并令

$$
G = \sum_{(\pi_1, \pi_2) \in A_k^2} \text{sgn}(\pi_1)\,\text{sgn}(\pi_2) \prod_{t=1}^{k} C[i_t, j_t]
$$

---

## 图 14 — 展开 $G$

其中

$$
\pi_1 = (i_1, i_2, \ldots, i_k), \qquad \pi_2 = (j_1, j_2, \ldots, j_k)
$$

$$
C[i_t, j_t] = \sum_{p=1}^{n} a[p, i_t]\, b[p, j_t]
$$

代入:

$$
G = \sum_{(\pi_1, \pi_2)} \text{sgn}(\pi_1)\,\text{sgn}(\pi_2) \prod_{t=1}^{k} \left(\sum_{p=1}^{n} a[p, i_t]\, b[p, j_t]\right)
$$

$$
G(\pi_1, \pi_2) = \text{sgn}(\pi_1)\,\text{sgn}(\pi_2) \prod_{t=1}^{k}\left(\sum_{p=1}^{n} a[p, i_t]\, b[p, j_t]\right)
$$

将连乘中的求和展开为对 $p \in N_n^k$ 的求和:

$$
= \text{sgn}(\pi_1)\,\text{sgn}(\pi_2) \sum_{p \in N_n^k} \prod_{t=1}^{k} a[p_t, i_t]\, b[p_t, j_t]
$$

令

$$
G(\pi_1, \pi_2, p) = \text{sgn}(\pi_1)\,\text{sgn}(\pi_2) \prod_{t=1}^{k} a[p_t, i_t]\, b[p_t, j_t], \qquad p = (p_1, p_2, \ldots, p_k)
$$

显然

$$
G = \sum_{(\pi_1, \pi_2) \in A_k^2} G(\pi_1, \pi_2) = \sum_{(\pi_1, \pi_2) \in A_k^2} \; \sum_{p \in N_n^k} G(\pi_1, \pi_2, p) = \sum_{\substack{(\pi_1, \pi_2) \in A_k^2 \\ p \in N_n^k}} G(\pi_1, \pi_2, p)
$$

---

## 图 15 — $G = H$(双射对应)

令

$$
S_G = \{G(\pi_1, \pi_2, p) \mid (\pi_1, \pi_2) \in A_k^2,\; p \in N_n^k\}
$$

$$
S_H = \{H(p, \pi_1, \pi_2) \mid p \in N_n^k,\; (\pi_1, \pi_2) \in A_k^2\}
$$

存在 $f: S_G \to S_H$,

$$
f(G(\pi_1, \pi_2, p)) = H(p, \pi_1, \pi_2), \qquad f^{-1}(H(p, \pi_1, \pi_2)) = G(\pi_1, \pi_2, p)
$$

$f$ 是双射,故 $\vert S_G \vert = \vert S_H \vert$,从而

$$
G = \sum_{g \in S_G} g = \sum_{h \in S_H} h = H
$$

**对 $A_k^2 / A_k$ 的性质,补充**:设

$$
\alpha = (a_1, a_2, \ldots, a_k), \qquad \beta = (b_1, b_2, \ldots, b_n)
$$

$\forall (\rho_1, \rho_2) \in \text{span}(\pi_e, \pi)$,记

$$
\rho_1 = (i_1, i_2, \ldots, i_k), \quad \rho_2 = (j_1, j_2, \ldots, j_k), \quad \pi = (n_1, n_2, \ldots, n_k)
$$

---

## 图 16 — 补充性质 7、8、9

令

$$
f(\rho_1, \rho_2, \alpha, \beta) = \text{sgn}(\rho_1)\,\text{sgn}(\rho_2) \prod_{t=1}^{k} a_{i_t}\, b_{j_t}
$$

下面成立:

**性质 7**:$\forall (\rho_1, \rho_2) \in \text{span}(\pi_e, \pi)$

$$
f(\rho_1, \rho_2, \alpha, \beta) = f(\pi_e, \pi, \alpha, \beta)
$$

**性质 8**:

$$
\sum_{(\rho_1, \rho_2) \in A_k^2} f(\rho_1, \rho_2, \alpha, \beta) = k! \cdot f(\pi_e, \pi, \alpha, \beta) = k! \cdot \text{sgn}(\pi) \prod_{t=1}^{k} a_t\, b_{n_t}
$$

**性质 9**:$M_1, M_2$ 为 $n \times k$ 矩阵,$n \geq k$。$\pi \in A_k$,$M \circ \pi$ 表示按照 $\pi$ 重排 $M$ 的列向量,则 $M \circ \pi = M\, T(\pi) = M R$,其中 $R = T(\pi)$。于是

$$
\det\big([M_1 \circ \pi]^T [M_2 \circ \pi]\big) = \det(M_1^T M_2)
$$

$$
\det\big((M_1 R)^T M_2 R\big) = \det(R^T M_1^T M_2 R)
$$

$$
= \det(R^T) \det(M_1^T M_2) \det(R)
$$

$$
= \det{}^2(R) \det(M_1^T M_2)
$$

$$
= \det(M_1^T M_2)
$$

回到

$$
H = \sum \det[M_1(p)] \det[M_2(p)]
$$

---

## 图 17 — 组合、排列与选行矩阵

$$
H = \sum_{p \in N_n^k} \det[M_1(p)] \det[M_2(p)]
$$

令

$$
A.N_n^k := \{p \in N_n^k \mid p = (p_1, \ldots, p_k),\; i \neq j \iff p_i \neq p_j\}
$$

$$
C.N_n^k := \{p \in N_n^k \mid p = (p_1, \ldots, p_k),\; p_i < p_{i+1},\; i \in N_{k-1}\}
$$

显然

$$
C.N_n^k \subseteq A.N_n^k \subseteq N_n^k
$$

$$
A.N_n^k = C.N_n^k \circ A_k = \{p \circ \pi \mid p \in C.N_n^k \wedge \pi \in A_k\}
$$

设 $B_n := [e_1^{(n)}, e_2^{(n)}, e_3^{(n)}, \ldots, e_n^{(n)}]$ 为 $\mathbb{R}^n$ 上的单位标准基。

$p \in N_n^k$,令 $T: N_n^k \to B_n^k$,$p = (p_1, p_2, \ldots, p_k)$,

$$
T(p) = [e_{p_1}^{(n)}, e_{p_2}^{(n)}, \ldots, e_{p_k}^{(n)}]
$$

$M(p)$ 表示从 $M$ 中选 $p_1, p_2, \ldots, p_k$ 行构成的方阵。令 $M \circ p = T(p) M$,不难验证

$$
M(p) = M \circ p = T(p) M
$$

---

## 图 18 — 将 $H$ 约化为组合求和,并定义 $G$

从对全体 $p \in N_n^k$ 的求和出发:

$$
H = \sum_{p \in N_n^k} \det(M_1 \circ p)\, \det(M_2 \circ p)
$$

当 $p$ 的指标出现重复时,$M \circ p$ 有两行相同,$\det(M \circ p) = 0$,故只保留指标互异的项 $p \in A.N_n^k$:

$$
H = \sum_{p \in A.N_n^k} \det(M_1 \circ p)\, \det(M_2 \circ p)
$$

由 $A.N_n^k = C.N_n^k \circ A_k$,将互异指标项拆为「组合 $p \in C.N_n^k$」与「列排列 $\pi \in A_k$」两重求和:

$$
H = \sum_{p \in C.N_n^k}\; \sum_{\pi \in A_k} \det(M_1 \circ p \circ \pi)\, \det(M_2 \circ p \circ \pi)
$$

而 $M \circ p \circ \pi = (M \circ p)\, T(\pi)$,故

$$
H = \sum_{p \in C.N_n^k}\; \sum_{\pi \in A_k} \det{}^2[T(\pi)]\, \det(M_1 \circ p)\, \det(M_2 \circ p)
$$

因 $\det{}^2[T(\pi)] = 1$,内层 $\sum_{\pi \in A_k}$ 恰好贡献 $\vert A_k \vert = k!$ 个相同的项:

$$
H = \sum_{p \in C.N_n^k} k!\, \det(M_1 \circ p)\, \det(M_2 \circ p)
$$

$$
H = k! \sum_{p \in C.N_n^k} \det(M_1 \circ p)\, \det(M_2 \circ p)
$$

即柯西-比内公式的右式 $= \dfrac{1}{k!} H$,亦即

$$
\sum_{p \in C.N_n^k} \det(M_1 \circ p)\, \det(M_2 \circ p) = \frac{1}{k!} H
$$

**定义 $G$**(公式左侧 $\det(M_1^T M_2)$ 按行列式展开):

$$
G = \sum_{(\pi_1, \pi_2) \in A_k^2} \text{sgn}(\pi_1)\,\text{sgn}(\pi_2)\, C_{i_1 j_1} C_{i_2 j_2} \cdots C_{i_k j_k}
$$

其中 $\pi_1 = (i_1, \ldots, i_k)$,$\pi_2 = (j_1, \ldots, j_k)$。令固定第一分量为 $\pi_e$、第二分量遍历 $A_k$ 的子和:

$$
G(\pi_e, A_k) = \sum_{\pi \in A_k} \text{sgn}(\pi_e)\,\text{sgn}(\pi)\, C_{1 j_1} C_{2 j_2} \cdots C_{k j_k}
$$

因 $\text{sgn}(\pi_e) = 1$:

$$
G(\pi_e, A_k) = \sum_{\pi \in A_k} \text{sgn}(\pi)\, C_{1 j_1} C_{2 j_2} \cdots C_{k j_k}
$$

---

## 图 19 — 最终得证

承接图 18,上式正是矩阵 $C = M_1^T M_2$ 的行列式的按列排列展开:

$$
G(\pi_e, A_k) = \sum_{\pi \in A_k} \text{sgn}(\pi)\, C_{1 j_1} C_{2 j_2} \cdots C_{k j_k} = \det(C) = \det(M_1^T M_2)
$$

记

$$
(\pi_e, A_k) = \{(\pi_e, \pi) \mid \pi \in A_k\}
$$

$$
(\pi_e, A_k) \circ \pi_1 = \{(\pi_e, \pi) \circ \pi_1 \mid \pi \in A_k\}
$$

由不变性

$$
G(\pi_e, \pi) = G[(\pi_e, \pi) \circ \pi_1]
$$

$$
G[(\pi_e, A_k) \circ \pi_1] = G[(\pi_e, A_k)] = \det(M_1^T M_2)
$$

对 $\pi \in A_k$ 求和:

$$
G = \sum_{\pi \in A_k} G[(\pi_e, A_k) \circ \pi] = \sum_{\pi \in A_k} \det(M_1^T M_2)
$$

$$
G = k! \, \det(M_1^T M_2)
$$

即柯西-比内公式左侧

$$
\det(M_1^T M_2) = \frac{1}{k!} G
$$

由 $G = H$,得

$$
\det(M_1^T M_2) = \frac{1}{k!} G = \frac{1}{k!} H
$$

$$
\sum_{p \in C.N_n^k} \det(M_1 \circ p)\, \det(M_2 \circ p) = \frac{1}{k!} H = \det(M_1^T M_2)
$$

$\blacksquare$ **得证。**

---

## 专业术语对照表

| 中文名称 | 英语简写 | 英语全称 |
|---------|---------|---------|
| 柯西-比内公式 | — | Cauchy–Binet formula |
| 双射 | — | Bijection |
| 群 | — | Group |
| 同构映射 | — | Isomorphism |
| 克罗内克记号 | — | Kronecker delta |
| 数学归纳法 | — | Mathematical induction |
| 排列(置换) | — | Permutation |

---

## References

[^1]: Horn, R. A., & Johnson, C. R. (2013). *Matrix Analysis* (2nd ed.), §0.8.7 (Cauchy–Binet formula). Cambridge University Press. — URL unverified
[^2]: Gantmacher, F. R. (1959). *The Theory of Matrices*, Vol. 1, Chapter I. Chelsea Publishing. — URL unverified
[^3]: Dummit, D. S., & Foote, R. M. (2004). *Abstract Algebra* (3rd ed.), Chapters 1–3 (对称群与置换的符号). John Wiley & Sons. — URL unverified
[^4]: Strang, G. (2016). *Introduction to Linear Algebra* (5th ed.), Chapter 5 (行列式与置换展开). Wellesley-Cambridge Press. — URL unverified

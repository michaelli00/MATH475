---
geometry: "left=1cm,right=1cm,top=1cm,bottom=2cm"
header-includes:
    - \usepackage{amsmath}
    - \usepackage{mathrsfs}
    - \usepackage{youngtab}
    - \DeclareMathOperator{\lcm}{lcm}
output: pdf_document
---

# The Basics - Permutations, Combinations, and General Counting

**$\mathbf{k}$-Permutation**: arrangement of $k$ elments from a set of $n$ elements $\quad \quad P(n, k) = \displaystyle \frac{n!}{(n-k)!}$

**Permutation With Repetition**: Can permute each object type $a_i !$ times $\quad \quad \displaystyle {n \choose a_1, a_2, \ldots, a_k} = \frac{n!}{a_1! \cdots a_k!}$

**Combination**: Total number of ways to create a $k$-element subset of $[n]$ $\quad \quad \displaystyle {n \choose k} = \frac{P(n, k)}{k!}$

- This comes from being able to permute the $k$-subset $k!$ ways

**Binomial Theorem**: $\displaystyle (x+y)^n = \sum_{k=0}^{n} \displaystyle {n \choose k} x^k y^{n-k}$

**Multinomial Theorem**: $\displaystyle (x_1 + \cdots + x_k)^n = \sum_{\substack{a_1 + \cdots + a_k = n \\ a_1, \ldots, a_k \geq 0}}^{}{n \choose a_1, a_2, \ldots, a_k} x_1^{a_1} \cdots x_k^{a_k}$

**Pigeon Hole Principle**: If $n$ pigeons are placed into $k$ holes, then at least one hole has

- At most $\displaystyle \lfloor \frac{n-1}{k} \rfloor$ (round down)
- At least $\displaystyle \lceil \frac{n}{k} \rceil$ (round up)

**Weak Composition**: Ordered $k$-tuple $(a_1, \ldots, a_k)$ such that $a_i \geq 0$ and $\displaystyle \sum_{i=1}^{k}a_i = n \quad \quad \displaystyle {n+k-1 \choose k-1}$

**Compositions**: Ordered $k$-tuple $(a_1, \ldots, a_k)$ such that $a_i \geq 1$ and $\displaystyle \sum_{i=1}^{k}a_i = n \quad \quad \displaystyle {n-1 \choose k-1}$

**Partition of $\mathbf{[n]}$**: $\{A_1, \ldots, A_k\}$ such that blocks are pairwise disjoint and $\displaystyle \bigcup_{i=1}^k A_i = X \quad \quad S(n, k) = S(n-1, k-1) + kS(n-1, k)$

**Bell's Number**: Total number of partitions of $[n]$ into any sized blocks $\displaystyle \quad \quad B(n) = \sum_{k=1}^{n} S(n, k) = \sum_{i=1}^{n}\displaystyle {n-1 \choose i-1}B(n-i)$

**Partition of $\mathbf{n}$**: $(a_1, \ldots, a_k)$ such that $a_1 \geq \cdots \geq a_k$ and $\displaystyle \sum_{i=1}^{k} a_i = n \quad \quad$ total: $p(n) \quad \quad$ $k$-parts: $p_k(n) = p_{k-1}(n-1) + p_k(n-k)$

- Represented using **Ferrers Diagram**: partial rectangular grid with $k$ rows, each with $a_i$ squares (conjugate is also valid)


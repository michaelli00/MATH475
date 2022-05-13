---
geometry: "left=1cm,right=1cm,top=1cm,bottom=2cm"
header-includes:
    - \usepackage{amsmath}
    - \usepackage{mathrsfs}
    - \usepackage{youngtab}
    - \usepackage{centernot}
    - \DeclareMathOperator{\lcm}{lcm}
output: pdf_document
---

**Permutation**: $P(n, k) = \displaystyle \frac{n!}{(n-k)!} \quad$ **Permutation w/ Rep**: $\displaystyle {n \choose a_1, a_2, \ldots, a_k} = \frac{n!}{a_1! \cdots a_k!} \quad$ **Combination**: $\displaystyle {n \choose k} = \frac{P(n, k)}{k!}$

**Binomial Theorem**: $\displaystyle (x+y)^n = \sum_{k=0}^{n} \displaystyle {n \choose k} x^k y^{n-k} \quad$ **Multinomial Theorem**: $\displaystyle (x_1 + \cdots + x_k)^n = \sum_{\substack{a_1 + \cdots + a_k = n \\ a_1, \ldots, a_k \geq 0}}^{}{n \choose a_1, a_2, \ldots, a_k} x_1^{a_1} \cdots x_k^{a_k}$

**Weak Composition**: $\displaystyle {n+k-1 \choose k-1} \quad \quad$ **Composition**: $\displaystyle {n-1 \choose k-1}$

**Stirling Number**: $S(n, k) = S(n-1, k-1) + kS(n-1, k) \quad \quad$ **Bell Number**: $B(n) = \sum_{k=1}^{n} S(n, k) = \sum_{i=1}^{n}\displaystyle {n-1 \choose i-1}B(n-i)$

- **Surjective Functions**: $k!S(n, k)$

**Partition of $\mathbf{n}$**: $(a_1, \ldots, a_k)$ such that $a_1 \geq \cdots \geq a_k$ and $\displaystyle \sum_{i=1}^{k} a_i = n \quad \quad$ total: $p(n) \quad \quad$ $k$-parts: $p_k(n) = p_{k-1}(n-1) + p_k(n-k)$

- Represented using **Ferrers Diagram**: partial rectangular grid with $k$ rows, each with $a_i$ squares (conjugate is also valid)

**Twelvefold Way Counting**

- $n$ labeled balls into $k$ labeled bins: $\quad k^n \quad \quad k!S(n, k) \quad \quad P(n, k)$

- $n$ unlabeled balls into $k$ labeled bins: $\displaystyle {n + k -1 \choose k - 1} \quad \quad \displaystyle {n-1 \choose k-1} \quad \quad \displaystyle {k \choose n}$

- $n$ labeled balls into $k$ unlabeled bins: $\sum_{i = 1}^k S(n, i) \quad \quad S(n, k) \quad \quad 1$

- $n$ unlabeled balls into $k$ unlabeled bins: $\sum_{i = 1}^k p_i(n) \quad \quad p_k(n) \quad \quad 1$

**Inclusion-Exclusion Principle**: $| \bigcap_{i = 1}^n \bar{A_i} \big| = |X| - \sum_{I \subseteq [n]}^{}(-1)^{|I|}|A_I|$

**Power Series Formulas**: $\displaystyle \sum_{n=0}^{\infty} x^n = \frac{1}{1-x} \quad \quad$ **OGF**: $\sum_{n=0}^{\infty} a_n x^n$

**Weak Compositions OGF**: $\displaystyle \frac{1}{(1-x)^k} = (1+x + \cdots) (1 + x + \cdots) \cdots = \sum_{n=0}^{\infty} \displaystyle {n+k-1 \choose k-1}x^n$

**Stirling Number OGF**: $\displaystyle \frac{x^k}{(1-x)(1-2x) \cdots (1-kx)} = \sum_{n=0}^{\infty} S(n, k) x^n \quad \quad$

**Partitions OGF**: $\displaystyle \frac{1}{(1-x)(1-x^2) \cdots} = \sum_{n=0}^{\infty} p(n) x^n \quad \quad \frac{x^k}{(1-x)(1 - x^2) \cdots} = \sum_{n=0}^{\infty} p_k(n) x^n$

**Catalan Numbers**: $\displaystyle C_n = \sum_{i=0}^{n-1}C_i C_{n-i-1} \quad \quad$ **OGF Catalan Numbers**: $C_n = \frac{\displaystyle {2n \choose n}}{n+1} \quad \quad C_0 = 0$

**Theorem**: $G$ is bipartite if and only if $G$ has no odd cycles

**Theorem**: $G$ with size $m$ has $\displaystyle \sum_{v \in V(G)}^{} \deg(v) = 2m \quad \quad$ **Corollary**: $G$ must have an even number of odd degree vertices

**Theorem**: There exists a $d$-regular graph on $n$ vertices if and only if at least one of $d, n$ is even

**Theorem**: $G$ with degrees $d = d_1, \ldots, d_n$ exists if and only if $s_1 = d_2 - 1, d_3 - 1, \ldots, d_{d_1 + 1} - 1, d_{d_1+2}, \ldots, d_n$ is graphical

**Theorem**: Every tree on $2$ or more vertices has at least $2$ leaves

**Theorem**: $G$ is a tree $\iff G$ is connected, acyclic with $n-1$ edges $\iff$ there is a unique path for $u, v \in V(G)$
**Theorem**: A connected graph of order $n$ has at least $n-1$ edges

**Theorem**: An edge $e$ is a bridge if and only if $e$ isn't in any cycles

**Spanning Tree to Code**: Delete lowest index leaf and write down vertex adjacent to it. Repeat until only an edge remains

**Code to Spanning Tree**: Find smallest index $b_1$ not used and create $a_1 \sim b_1$. Delete $a_1$ and append $b_1$. Repeat until $b_1, \ldots, b_{n-2}$ then connect missing $2$ indices

**Theorem**: Each Prufer code corresponds to a unique spanning tree. Thus number of spanning trees of $K_n$ is $n^{n-2}$

**Corollary**: Total spanning trees such that vertex $i$ has degree $d_i$ is $\displaystyle {n-2 \choose d_1 - 1, d_2 - 1, \ldots}$

**Rooted Plane Tree**: Tree with a root vertex, left/right ordering, but vertices are NOT labeled

- Clockwise walk around border of the tree reveals that the number of rooted plane trees on $n+1$ vertices is $\displaystyle C_n = \frac{\displaystyle {2n \choose n}}{n+1}$

**Rooted Forest**: Forest where each tree component has a distinguishable root vertex

**Theorem**: Number of labeled rooted forests on $n$ vertices is $(n+1)^{n-1}$

**Matching**: Set of edges with no shared endpoints

**Hall's Theorem**: A bipartite graph $G$ has a matching that saturates $A$ if and only if for all $S \subseteq A, |N(S)| \geq |S|$

**k-factor**: Spanning k-regular subgraph $\quad \quad$ **k-factorable**: Exists factors $F_1, \ldots, F_k$ that decompose $E(G)$ into disjoint sets

- **Note**: $G$ is 1-factorable if and only if $G$ has a perfect matching $\quad \quad$ 2-factor is just a union of cycles

- **Note**: Any k-regular bipartite graph has a perfect matching

**SDR**: Given sets $A_1, \ldots, A_n$ (not necessarily distinct), it is an **SDR** if there are $n$ distinct elements such that $a_i \in A_i$

**Theorem**: Let $G$ be a connected graph. Then $G$ is Eulerian if and only if every vertex has an even degree

**Corollary**: Graph $G$ has a **Eulerian Trail** $\iff 2$ vertices have odd degree, which are the start and end of the trail

**Hamiltonian Cycle**: A cycle (vertices are used only once except the start/end) that contains all vertices of $G$

**t-tough**: A graph is $t$-tough if $\displaystyle t \leq \frac{|S|}{c(G \setminus S)}$ where $S$ runs through all subsets of vertices that disconnect $G$

**Theorem**: If $G$ is Hamiltonian, then $t(G) = \displaystyle \frac{|S|}{c(G \setminus S)} \geq 1$, i.e. $\forall$ disconnecting set $S$, $|S| \geq c(G \setminus S)$

- **Corollary**: If there exists a subset of vertices where $\displaystyle |S| < c(G \setminus S)$, then the graph is not Hamiltonian

**Theorem (Ore)**: Let $G$ have order $n \geq 3$. If $\deg(u) + \deg(v) \geq n$ for any $2$ non-adjacent vertices, then $G$ is Hamiltonian

- **Note**: This is a sufficient but NOT necessary condition. Consider $C_n$, non-adjacent vertices have degree $\deg(u) + \deg(v) < n$

**Euler's Identity**: If $G$ is a connected, planar graph on $n$ vertices, $m$ edges, and $f$ faces, then $n - m +f = 2$

**Theorem**: For a connected planar graph of order $\geq 3$, we have $m \leq 3n - 6$

- **Corollary**: If $G$ is planar, then there is a vertex of degree $\leq 5$

**Keratowski Theorem**: $G$ is planar if and only if $G$ doesn't contain $K_5$ or $K_{3, 3}$, or a subdivision of either

**Independence Number**: Size of largest independet set, denoted $\alpha(G)$

- **Note**: k-chromatic $\implies$ $V(G)$ can be partitioned into $k$ independent sets (color classes)

**Theorem**: $\chi(G) = 2$ if and only if $G$ is non-empty bipartite graph $\quad \quad$ **Corollary**: If $G$ has an odd cycle, then $\chi(G) \geq 3$

**Theorem**: $\chi(G) \geq \omega(G) \quad \quad \chi(G) \geq \frac{n}{\alpha(G)}$

**Theorem**: $\chi(G) \leq \Delta(G) + 1 \quad \quad$ **Brooks' Theorem**: For a connected graph not equal to odd $C_n$ or $K_n$, $\chi(G) \leq \Delta(G)$

**Mycielski Construction**: Maintain $\omega(G) = 2$ while arbitrarily grow $\chi(G)$ by adding $n+1$ vertices ($w, u_1, \ldots, u_n$)

 - Join $w$ to all $u_i$ such that $u_i$'s are not adjacent to each other. Join $u_i$ with $v_j$ where $v_j \sim v_i$

**Ramsey Number**: $R(s, t) = N$, we must show that

1. $K_{N-1}$ has the existence of a coloring with no blue $K_s$ or red $K_t$

    - Showing the existence of a color $\alpha$ with no red $K_s$ and blue $K_t$ in $K_m$ shows that $R(s, t) > m$

2. For any edge coloring of $K_N$, there is always a red $K_s$ or blue $K_t$

    - Showing that all colorings have a red $K_s$ or blue $K_t$ in $K_m$ shows that $R(s, t) \leq m$

**Mantel Theorem**: $G$ on $n$ vertices with $m$ edges and no $K_3$ satisfies $m \leq \lfloor \frac{n^2}{4} \rfloor$

**Turan Graph**: r-partite graph such that each partite set has nearly the same size $\quad \quad$

**Turan Theorem**: Turan graph $T_{n, r}$ doesn't contain a $K_{r + 1}$ subgraph and has the max number of edges

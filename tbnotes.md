---
title: "MATH475: Combinatorics and Graph Theory"
author: Michael Li
geometry: "left=1cm,right=1cm,top=1cm,bottom=2cm"
header-includes:
    - \usepackage{amsmath}
    - \usepackage{mathrsfs}
    - \DeclareMathOperator{\lcm}{lcm}
output: pdf_document
---

# Basic Methods

## Addition and Subtraction

**Theorem 1.1 - Addition Principle**: If $A, B$ are 2 disjoint finite sets, then $|A \cup B| = |A| + |B|$

*Proof*: Both sounds count the number of elements in $A \cup B$

LHS directly counts the number of elements whereas RHS counts the number of elements in $A$ and the number of elemnets in $B$

Since $A, B$ are disjoint, LHS equals RHS

&nbsp;

**Theorem 1.2 - Generalized Addition Principle**: Let $A_1, \ldots, A_n$ be disjoint, finite sets. Then $|A_1 \cup \cdots \cup A_n| = |A_1| + \cdots + |A_n|$

*Proof*: similar to the proof of Theorem 1.1, both sides count the number of elements in $A_1 \cup \cdots \cup A_n$.

Since these sets are djsoint, LHS equals RHS

&nbsp;

**Theorem 1.4 - Subtraction Principle**: Let $A$ be a finite set and $B \subseteq A$. Then $|A - B| = |A| - |B|$

*Proof*: First we show that $|A - B| + |B| = |A|$. Note that $A-B, B$ are disjoint and their union is $A$

Both sides count the number of elements in $A$

- LHS first counts the elements not in B then those in B
- RHS counts the elements directly

Thus $|A - B| + |B| = |A| \implies |A-B| = |A| - |B|$

- **Note**: We must have $B \subseteq A$ otherwise their union has elements NOT in $A$

## Multiplication

**Theorem 1.6 - Product Principle**: Let $X, Y$ be finite sets. The number of pairs $(x, y)$ satisfying $x \in X$ and $y \in Y$ is $|X| \times |Y|$

*Proof*: There are $|X|$ choices for $x$, each of which has $|Y|$ choices for $y$

&nbsp;

**Theorem 1.8 - Generalized Product Principle**: Let $X_1 \ldots, X_k$ be finite sets. The number of k-tuples $(x_1, \ldots, x_k)$ satisfying $x_i \in X_i$ is $|X_1| \times \cdots \times |X_k|$

*Proof by Induction*: Base case clearly holds for $k = 1$. Base case for $k= 2$ by Theorem 1.6

IH: Assume the statement holds for $k-1$

IS: Prove the statement for $k$

$(x_1, \ldots, x_k)$ can be decomposed into an ordered pair $((x_1, \ldots x_{k-1}), x_k)$ which has $x_i \in X_i$

The number of elements satisfying the $(k-1)$ tuple, by IH is $|X_1| \times \cdots \times |X_{k-1}|$.

The number of elements satisfying $x_k \in X_k$ is $|X_k|$.

Thus by the product principle, the number of k-tuples satisfying the condition is $(|X_1| \times \cdots \times |X_{k-1}|) \times |X_k|$

&nbsp;

**Example**: How many 4-digit positive integers both start and end on an even number

- first digit $\in \{2, 4, 6, 8\}$
- second digit $\in \{0, \ldots, 9\}$
- third digit $\in \{0, \ldots, 9\}$
- foruth digit $\in \{0, 2, 4, 6, 8\}$

Thus answer is $4 * 10 * 10 * 5 = 2000$

&nbsp;

**Corollary 1.11**: The number of k-letter strings over an n-element alphabet $A$ is $n^k$

*Proof*: Apply Theorem 1.8 with $X_1 = X_2 = \cdots = A$

&nbsp;

**Note**: Notationwise, $[n] = \{1, 2, \ldots, n\}$

**Theorem 1.15**: For an $n \in Z^{+}$, the number of ways to arrange all elements of $[n]$ is $n!$

*Proof*: There are $n$ ways to select the first element, $n-1$ ways to select the second element, $\ldots$

Applying the Product Principle, we get the desired result $n!$

&nbsp;

**Definition - Permutation**: List of each elements in $S$ that appear exactly once

&nbsp;

**Theorem 1.17**: Let $n, k \in Z^{+}$ such that $n \geq k$. Then the number of ways to make a k-element list from $[n]$ without repeating any elements is
$$(n)_k = (n)(n-1) \cdots (n-k+1)$$
*Proof*: $n$ choices for the first element, $\ldots$, $n-k +1$ choices for the kth element

&nbsp;

**Example**: If we go north, we can visit 4 out of 10 schools. If we go south, we can visit 5 out of 8 schools. Assuming we can only go one way, how many different itineraries can we set up?

$(10)_4 + (8)_5 = 5040 + 6720 = 11760$

## Division

**Definition - d-to-One Function**: Let $S, T$ be a finite sets and $d$ be a fixed integer. Then a function $f: T \rightarrow S$ is a d-to-one function if for each $s \in S$, there are $d$ elements in $T$ such that $f(t) = s$

&nbsp;

**Theorem 1.21 - Division Principle**: Let $S, T$ be finite sets such that $f: T \rightarrow S$ is d-to-one. Then $|S| = \frac{|T|}{d}$

*Proof*: results from the definition of d-to-one functions

&nbsp;

**Example**: Number of different seatings for $n$ people at a circular table is $(n-1)!$

If the table were linear, then there are $n!$ arrangements.

Let $T$ be the number of arrangements on a linear table and $S$ be the arrangements around a circular table.

Each $s \in S$ corresponds to $n$ different $t \in T$

Clearly $f: T \rightarrow S$ is n-to-one so by Division Principle $|S| = \frac{|T|}{n} = (n-1)!$

&nbsp;

**Theorem 1.23**: Let $n \in Z^{+}$ and $k \leq n$ be non-negative. Then the number of k-element subsets of $[n]$ is
$${n \choose k} = \frac{n(n-1) \cdots (n- k + 1)}{k!} = \frac{n!}{k!(n-k)!}$$

*Proof*: The number of ways to make a k-element list from $[n]$ is $(n)_k$

Since each k-element subset has $k!$ ways of being listed, each k-subset will be counted $k!$ times in $(n)_k$

Thus by Division Principle, the number of k-subsets is $\frac{(n)_k}{k!}$

&nbsp;

**Definition - Binomial Coefficients**: Values of ${n \choose k}$

&nbsp;

**Theorem 1.24 Binomial Theorem**: Let $n \in Z^{+}$. Then $(x+y)^n = \sum_{n=0}^n {n \choose k} x^k y^{n-k}$

*Proof*: LHS is the product of $(x+y)$ $n$ times

RHS takes a term ($x$ or $y$) from each of the $n$ factors and multiplies the selected terms ($2^n$ possibilities) and add all of the $2^n$ sums

The sum $x^k y^{n-k}$ appears ${n \choose k}$ times since we chose $x$ from $k$ factors (${n \choose k}$ ways of doing this) and $y$ receives the remaining factors

&nbsp;

**Example**: Given $110$ bus lines and a machine that punches either 2 or 3 holes on a ticket within some of the 9 numbered squares, can a city set up machines such that each line will punch the tickets differently?

${9 \choose 2} + {9 \choose 3} = 36 + 84 = 120 > 110$. Thus the city can punch the ticket differently for each bus line

## Applications of Basic Counting Principles

### Bijection

**Definition - Bijection**: A map $f: S \rightarrow T$ is called a **bijection** if it is one-to-one and onto

&nbsp;

**Corollary 1.28**: Let $S, T$ be finite sets. If a bijection $f: S \rightarrow T$ exists, then $|S| = |T|$

*Proof*: Follows from the Division Principle with $d = 1$

&nbsp;

**Example**: Consider the possible lattice paths from $(0, 0)$ to $(6, 4)$ moving only eastward and northward.

- Number of ways to reach $X = (6, 4)$ is ${10 \choose 6}$
- Number of ways to stop at $Y = (4, 2)$ and then $X = (6, 4)$ is ${6 \choose 4} {4 \choose 2}$
- Number of ways stop at $U = (3, 2)$ and $X = (6, 4)$ or stop at $V = (2, 3)$ and $X = (6, 4)$ is ${5 \choose 3} {5 \choose 3} + {5 \choose 2} {5\choose 4}$

The calculation above works because there is a bijection between the set $S$ of lattice paths and the set $T$ of six-element subsets of $[10]$

&nbsp;

**Proposition 1.29**: For $n \in Z^+$, the number of divisors of $n$ greater than $\sqrt{n}$ is equal to the number divisors less than $\sqrt{n}$

*Proof*: Let $S$ be the set of divisors of $n$ larger than $\sqrt{n}$ and $T$ be the set of divisors less than $\sqrt{n}$

Define $f: S \rightarrow T$ by $f(s) = n/s$

- For all $s \in S$, $s \cdot f(s) = n \implies f(s) \mid n$ and $f(s) < \sqrt{n} \implies f(s) \in T$. Thus $f$ is a function from $S$ into $T$
- Show that $f$ is one-to-one

  - For all $t \in T$, there is at least one $s \in S$ such that $f(s) = t$, namely $s = n/t$
  - On the other hand, if $f(s) = t$, there is only one good $s$ since $s \cdot f(s) = n \implies s t = n \implies s = n/t$

Thus we have shown $f$ is a bijection and thus $|S| = |T|$

&nbsp;

**Upshot**: Steps to show a bijection exists

1. Define a function $f$ from $S$ into $T$
2. Show that for all $s \in S$, $f(s) \in T$ holds
3. Show that for all $t \in T$, there is only one $s \in S$ that satisfies $f(s) = t$
   - Show there at least one $s$ satisfying $f(s) = t$
   - Show that there is at most one $s$ satisfying $f(s) = t$

&nbsp;

**Lemma 1.32**: The number of lattice paths from $(0, 0)$ to $(n, n)$ that never go above the line $x = y$ is equal to the number of ways to fill a $2 \times n$ (Standard Young Tableaux) grid such that each row and column is increasing (right, down)

*Proof*: Let $S$ be the set of all lattice paths from $(0, 0)$ to $(n, n)$ that do not go above the line $y = x$ and $T$ be the set of all Standard Young Tableaux



- Take $s \in S$. Let $e_1, e_2, \ldots, e_n$ denote the positions of the $n$ east steps of $s$ and $n_1, n_2, \ldots, n_n$ denote the $n$ north steps of $s$

    The ith east/north step always occur before the (i+1)th east/north step. Thus rows are horizontally increasing.

    We also have $n_j < e_j$ since otherwise we would be above the main diagonal. Thus columns are also increasing.

    Thus we have shown that for all $s \in S, f(s) \in T$ holds
- Take $t \in T$ If there is an $s \in S$ such that $f(s) = t$, then $s$ has to be the lattice path whose east steps correspond to the first row of $t$ and whose north steps correspond to the second row of $t$

    On the other hand, this lattice path $s$ never goes above the main diagonal by the increasing property of the columns

Thus we have shown that $f$ is a bijection

### Binomial Coefficients

**Proposition 1.35**: For $k \leq n, {n \choose k} = {n \choose n -k }$

*Proof 1*: ${n \choose k}$ can be looked as all possible lattice paths from $(0,0)$ to $P = (k, n-k)$

Similarly, ${n \choose n-k}$ can be looked as all possible lattice paths from $(0,0)$ to $Q = (n-k, k)$

We can define a bijection using a reflection over $y = x$

This will map $OP$ paths to $OQ$ paths in a bijective fashion

*Proof 2*: LHS counts the number of $k$-element subsets of $[n]$, and RHS counts the number of $n-k$-element subsets of $[n]$

Let $S$ be the set of $k$-subsets and $T$ be the set of $n-k$-subsets

We can define the mapping $f(A) = A^c$ which takes the complement of $A \in S$

For all $A \in S$, clearly $f(A)$ is a $n-k$ element subset. Thus $f(A) \in T$

Furthermore, if $B \in T$, then there is exactly one $A \in S$ satisfying $f(A) = B$, namely $A = B^c$

Thus $f$ is a bijection from $S$ to $T$. Thus $|S| = |T|$

&nbsp;

**Note**: $\displaystyle 2^n = \sum_{k=0}^n {n \choose k}$

**Note**: ${n \choose k}$ form the nth row of Pascal's Triangle

**Theorem 1.36**: $\displaystyle {n \choose k} + {n \choose k + 1} = {n + 1 \choose k}$

*Proof 1*: RHS counts the number of lattice paths to $R = (k+1, n-k)$

LHS counts the number of paths to $R$ via $U = (k, n-k)$ or $V = (k + 1, n - k - 1)$

*Proof 2*: RHS counts the number of $k+1$-element subsets of $[n + 1]$

LHS counts the number of $k+1$-element subsets WITH and WITHOUT the new element $n+1$. The remaining $k$ come from $[n]$

&nbsp;

**Example 1.38**: $\displaystyle \sum_{k = 1}^n k {n \choose k}^2 = n {2n - 1 \choose n - 1}$

*Solution*: We can look at this problem as trying to form a committee of $n$ people from $n$ partners and $n$ associates, with a president who is on the committee and a partner

RHS selects one president from $n$ partners ($n$ ways of doing this). Then selects the remaining $n-1$ members on the committee (${2n-1 \choose n-1}$ ways of doing this)

LHS selects $k$ partners (${n \choose k}$ ways of doing this), selects a president from these selected partners ($k$ ways of doing this), and then selects the remaining $n-k$ associates (${n \choose n-k} = {n \choose k}$ ways of doing this)

&nbsp;

**Example 1.39**: For $\displaystyle n \geq 2, n(n-1) 2^{n-2} = \sum_{k = 2}^{n}{n \choose k} k (k-1)$

*Solution*: We can view this problem as selecting a committee of at least $2$ people (including a president and a vice president) from a group of $n$ people

LHS selects the president and the vice president ($n(n-1)$ ways of doing this), and then looks at the possible subsets of people from a group of $n-2$ people ($2^{n-2}$ possible subsets)

RHS selects a committee of $k$ people (${n \choose k}$ ways of doing this), and then selects a president and vice president from this committee ($k(k-1)$ ways of doing this)

### Permutation with Repetition

**Theorem 1.41**: Suppose we want to arrange $n$ objects in a line with $k$ different types of objects that are indistinguishable from each other. Let $a_i$ be the number of objects of type $i$. Then the total number of arrangements is
$$\frac{n!}{a_1! a_2! \cdots a_k!}$$

*Proof 1*: If we ignore the object types, then there are $n!$ ways to arrange $n$ objects

We can permute each object amongst its own type. Thus for any arrangement, there are $a_1! a_2! \cdots a_k!$ identical arrangements

Thus using the division principle, we see that the total number of indistinguishable arrangements is $\frac{n!}{a_1! a_2! \cdots a_k!}$

*Proof 2*: The arrangement of $n$ objects with $k$ different types is determined by the positions of $a_1$ objects of type $1$, $a_2$ objects of type $2$, $\ldots$

There are ${n \choose a_1}$ choices for positioning objects of type 1, ${n - a_1 \choose a_2}$ choices for positioning objects of type 2, $\ldots$, ${a_k \choose a_k} = 1$ choices for positioning objects of type $k$

Thus we see
$${n \choose a_1} {n - a_1 \choose a_2} \cdots {a_k \choose a_k} = \frac{n!}{a_1! a_2! \cdots a_k!}$$

&nbsp;

**Definitino - Multinomial coefficient**: $\displaystyle {n \choose a_1, a_2, \ldots, a_k} = \frac{n!}{a_1! a_2! \cdots a_k!}$

- **NOTE**: ${n \choose a_1, a_2} = {n \choose a_1} = {n \choose a_2}$

&nbsp;

**Example**: Suppose a person wants to visit 4 factories $A, B, C, D$ twice over $8$ days. How many different orders can the person visit, with the restriction that he doesn't visit factory $A$ on 2 consecutive days

*Solution*: Ignoring the restriction on factory $A$, we have $\displaystyle {8 \choose 2, 2, 2, 2} = 2520$

To consider the restriction on $A$, let's treat $A$ and $A'$ as one single unit. Thus we have $\displaystyle {7 \choose 1, 2, 2, 2} = 630$

Thus there are $2520 - 630 = 1890$ possible orderings that meet the criteria

## Pigeonhole Principle

**Theorem 1.44 Pigeonhole Principle**: Let $A_1, A_2, \ldots, A_k$ be pairwise disjoint finite sets and $|A_1 \cup A_2 \cup \cdots \cup A_k| > kr$. Then there exists at least one index $i$ such that $|A_i| > r$

*Proof by Contradiction*: Assume that for all $i$, $|A_i| \leq r$. Then we have $|A_1 \cup A_2 \cup \cdots \cup A_k|  = |A_1| + |A_2| + \cdots + |A_k| \leq kr$ which contradicts are assumption

Thus we must have at least one index $i$ such that $|A_i| > r$

&nbsp;

**Example**: Consider the sequence $a_i = 2^i - 1$ and let $q$ be an odd integer. Then the sequence has an element divisible by $q$

*Solution*: Consider the first $q$ elements of the sequence. If one is divisible by $q$, we are done

Otherwise consider the remainder of these elements mod $q$
$$a_i = d_iq + r_i$$
Since $r_i \in (0, q)$, by PHP, there are at least 2 elements $a_n, a_m$ that share the same remainder

Thus $a_n - a_m = (d_n - d_m)q = (2^n - 1) - (2^m - 1) = 2^m(2^{n-m} - 1) = 2^m a_{n-m}$

Since $2^m$ and $q$ are relatively prime, we must have that $q \mid a_{n-m}$

&nbsp;

**Example**: Suppose we select $n+1$ distinct integers from $[2n]$. Then

- There is at least one pair that has sum $2n + 1$
- There is at least one pair that has difference of $n$

*Solution*:

- Split $[2n]$ into $n$ subsets $\{i, 2n + 1 - i\}$. Since we chose $n + 1$ elements, by PHP $2$ of the elements must lie in the same subset. Thus clearly $i + 2n + 1 - i = 2n + 1$
- Split $[2n]$ into $n$ subsets $\{i, n + i\}$. Since we chose $n + 1$ elements, by PHP $2$ of the elements must lie in the same subset. Thus clearly $n+ i - i = n$

# Application of Basic Methods

## Multiset/Composition

**Definition - Multiset**: collection that allows for repetition of elements

- A multiset is determined by the multiplicities of each element

**Definition - Weak Composition**: Let $a_1, a_2, \ldots, a_k \geq 0$ such that $\displaystyle \sum_{i=1}^{k}a_i = n$. Then the ordered tuple $(a_1, a_2, \ldots, a_k)$ is a **weak composition** of $n$ into $k$ parts

- **Note**: There is a bijection between weak compositions of $[n]$ into $k$ parts AND $n$-element multisets over a $k$-element set

&nbsp;

**Theorem 2.2**: The number of weak compositions of $[n]$ into $k$ parts is ${n+k-1 \choose n} = {n + k - 1 \choose k - 1}$

*Proof*: Consider $n$ balls distributed across $k$ boxes. Each distribution is equivalent to a weak composition

To count the ways of distributing balls, we can insert a wall between each box $i$ and $i+ 1$

- Each distribution corresponds with arrangement of $n$ balls and $k-1$ walls
- Conversely, each arrangement corresponds to a unique distribution of balls

Thus the number of ways to arrange $n$ balls and $k-1$ walls is ${n+k-1 \choose k-1}$

${n+k-1 \choose n} = {n + k - 1 \choose k - 1}$ follows from Proposition 1.35

&nbsp;

**Definition - Composition**: Let $a_1, a_2, \ldots, a_k \in Z^+$ such that $\displaystyle \sum_{i=1}^{k}a_i = n$. Then the ordered tuple $(a_1, a_2, \ldots, a_k)$ is a **composition** of $n$ into $k$ parts

- **Note**: compositions involve only positive integers, whereas weak compositions allow numbers to be $0$

&nbsp;

**Corollary 2.5**: The number of compositions of $n$ into $k$ parts is ${n-1 \choose k-1}$

*Proof*: We show a bijection exists from $W$, the set of weak compositions of $n-k$ into $k$ parts, into $C$, the set of compositions of $n$ into $k$ parts.

Simply add an additional element to each part, assuring that each part will have a positive size. Thus the bijection shows $|W| = |C|$

From Theorem 2.2, we see that $|W| = {n -k +k - 1 \choose k - 1} = {n - 1 \choose k - 1} = |C|$

## Set Partitions

**Definition - Blocks**: Let $k \leq n$ and let $B = \{B_1, \ldots, B_k\}$ where $B_i \subseteq [n]$ and each $B_i$ are non-empty and pairwise disjoint where $\bigcup_{i=1}^k B_i = [n]$. Then $B$ is a partition of $[n]$ into $k$ **blocks**

&nbsp;

**Example**: Find the number of partitions of $[5]$ into $3$ blocks

*Solution*: Possible block sizes are 3-1-1 or 2-2-1

- Possibilities of selecting $3$ blocks is ${5 \choose 3} = 10$ ways. The last 2 singleton blocks are automatically determined. Thus this results in $10$ possible arrangements
- $5$ choices for singleton blocks, and ${4 \choose 2}$ choices for the first doubleton. The last doubleton is automatically determined but we need to divide by $2$ to consider double counting. Thus this results in $15$ possible arrangements

Thus we have total number of arrangements is $25$

&nbsp;

**Definition - Stirling Number of the Second Kind**: Number of partitions of $[n]$ into $k$ blocks denoted $S(n, k)$

- If $k > n$ then $S(n, k) = 0$
- If $n > 0$ then $S(n, 0) = 0$
- $S(0, 0) = 1$
- $S(n, 1) = S(n, n) = 1$

&nbsp;

**Theorem 2.10**: For $n \geq k, S(n, k) = S(n-1, k-1) + kS(n-1, k)$

*Proof*: LHS counts all partitions of $[n]$ into $k$ blocks

RHS counts 2 classes of arrangements

- The element $n$ is by itself. Then we look at $S(n-1, k-1)$, the number of partitions of $[n-1]$ into $k-1$ blocks
- The element $n$ is NOT by itself. The remaining $n-1$ elements are partitioned in $k$ blocks ($S(n-1, k)$). And then there are $k$ ways to place the element $n$

&nbsp;

Let $h(n, k)$ be the sum of all ${n-1 \choose k-1}$ products that consist of $n-k$ factors such that all of these factors are elements of $[k]$

**Examples**:

- For $n = 4, k = 2$, h(4, 2) = 1 *1 + 1*2 + 2 *2 = 7 = S(4, 2)$
- For $n = 4, k = 3, h(4, 3) = 1 + 2 + 3 = 6 = S(4, 3)$

&nbsp;

**Lemma 2.14**: $h(n, k) = h(n-1, k-1) + kh(n-1, k)$

*Proof*: LHS is the sum of all $(n-k)$-factor products from $[k]$

RHS splits into 2 classes

- Those that contain the factor $k$. These also contain an $(n-k-1)$-factor product over the set $[k]$. Summing all of these products, we get $kh(n-1, k)$
- Those that do not contain $k$. This is handled by $h(n-1, k-1)$

&nbsp;

**Example**: For $n = 4, k = 2, h(4, 2) = 1 * 1 + 2*1 +2*2 = 1*1 + 2(1 + 2) = h(3, 1) + 2*h(3, 2)$

&nbsp;

**Theorem 2.11**: $h(n, k) = S(n, k)$

*Proof by Induction*:

Base case: $n + k = 0 \implies h(0, 0) = S(0, 0) = 1$ is clearly true

IH: Assume if $n+k \leq m$, then $S(n, k) = h(n, k)$

IS: Show for $n+k = m + 1$. Then we have
\begin{align*}
 S(n, k) &= S(n-1, k-1) + kS(n-1, k)\\
 &= h(n-1, k-1) + h(n-1, k)\\
 &= h(n, k)
\end{align*}

&nbsp;

**Theorem 2.16**: For $n \geq k, S(n+1, k) = \sum_{i=0}^{n}{n \choose i}S(n-i, k-1)$

*Proof*: LHS counts the number of partitions of $[n+1]$ into $k$ blocks

RHS counts the number of partitions of $[n+1]$ into $k$ blocks where the element $n+1$ is in a block of size $i+1$

- ${n \choose i}$ ways to choose $i$ elements to share a block with the element $n+1$
- Then there are $S(n-i, k-1)$ ways to partition the remaining $k-1$ blocks

&nbsp;

**Bell Number**: Number of all partitions of $[n]$, denote $B(n)$

| $n$ | $B(n)$ |
| ----| -------|
| $0$ | $1$    |
| $1$ | $1$    |
| $2$ | $2$    |
| $3$ | $5$    |
| $4$ | $15$   |
| $5$ | $52$   |
| $5$ | $52$   |
| $6$ | $203$  |
| $7$ | $877$  |
| $8$ | $4140$ |

**Theorem 2.18**: $\displaystyle B(n+1) = \sum_{k=0}^{n}B(k) {n \choose k}$

## Partitions of Integers

**Partition**: finite sequence $(a_1, a_2, \ldots, a_k)$ of positive integers such that $a_1 \geq a_2 \geq \cdots \geq a_k$ and $a_1 + a_2 + \cdots + a_k = k$. Then this sequence is called a **partition** of the integer $n$

- Number of partitions of $n$ is denoted $p(n)$

**Example**: For $n = 4$. There are $5$ partitions

- $(4), (3, 1), (2, 2), (2, 1, 1), (1, 1, 1, 1) \implies p(4) = 5$

**Theorem 2.21**: As $n \rightarrow \infty, p(n)$ satisfies
$$p(n) \approx \frac{1}{4\sqrt{3}}e^{\pi \sqrt{\frac{2n}{3}}}$$

**SKIPPING FERRERS SHAPES and EULER PENTAGONAL NUMBER THEOREM**

## Inclusion-Exclusion Principle

**Lemma 2.32**: $|A \cup B| = |A| + |B| - |A \cap B|$

*Proof*: LHS counts the number of elements in $|A \cup B|$

RHS also does the same but $|A| + |B|$ ends up double counting elements in both $A$ AND $B$. Subtracting by $|A \cap B|$ corrects this anomaly

&nbsp;

**Example**: Find the number of positive integers $\leq 300$ that are divisible by $2$ or $3$

*Solution*: Number of eligible integers divisible by $2$ is $300 / 2 = 150$

Number of eligible integers divisible by $3$ is $300/ 3 = 100$

Number of eligible integers that were double counted is $300 / 6 = 50$

Thus answer is $|A \cup B| = 150 + 100 - 50 = 200$

&nbsp;

**Example**: Suppose there are $30$ guests that we want to split into $3$ groups of $10$. However, guest $U$ cannot be in the same group as guest $V$, and guest $X$ cannot be in the same group as guest $Y$. How many possible arrangements are there?

*Solution*: First count the bad partitions of $[30]$ into $3$ blocks. When $1, 2$ are in the same block, when $3, 4$ are in the same block, or when both events occur

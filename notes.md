---
title: "MATH475: Combinatorics and Graph Theory"
author: Michael Li
geometry: "left=1cm,right=1cm,top=1cm,bottom=2cm"
header-includes:
    - \usepackage{amsmath}
    - \usepackage{mathrsfs}
    - \usepackage{youngtab}
    - \usepackage{mathtools}
    - \DeclareMathOperator{\lcm}{lcm}
output: pdf_document
---

\newpage

# Chapter 1

## The Basics - Permutations, Combinations, and General Counting

### Permutation

**Definition - Permutation**: A **permutation** of an $n$-element set is an arrangement of the elements in a specific order

- $k$-permutation: arrangement of $k$ elements from the set
- The total number of $k$-permutation of an $n$-element set is
$$P(n, k) = \frac{n!}{(n-k)!} = n(n-1) \cdots (n-k + 1)$$

&nbsp;

**Example**: 10 people can run for office for a committee with a President, Vice President, and Treasurer. The total number of possible committees is $P(10, 3)$

&nbsp;

**Definition - $\mathbf{k}$th Falling Factorial of $\mathbf{n}$**: Let $n \geq k$, both positive integers. Then the **$\mathbf{k}$th Falling Factorial of $\mathbf{n}$** is $(n)_k = n(n-1) \cdots (n- k + 1)$

&nbsp;


**Example - Permutations with Repetitions**: How many rearrangements of $AAAABBBCCD$ are there?

- If we were only looking at distinct elements, there would be $10!$ factorial. However, the elements aren't distinct

As an example, look at how we can reorder the $A$'s
$$A_1 A_2 A_3 A_4 BBBCCD = A_2A_1A_3A_4BBBCCD = \cdots$$
Thus there are $4!$ of these representations that are equivalent and we divide $10!$ by $4!$ to account for this. Similar idea for the other letters

Thus the number of rearrangements is $\displaystyle \frac{10!}{4!3!2!1!}$

&nbsp;

**Theorem**: Suppose object $1$ occurs $a_1$ times, object $2$ occurs $a_2$ times, $\ldots$, object $k$ occurs $a_k$ times. Furthermore, suppose $a_1 + \cdots + a_k = n$

Then the total number of arrangements if $\displaystyle \frac{n!}{a_1 ! \cdots a_k!} = {n \choose a_1, a_2, \ldots, a_k}$

- **Definition - Multinomial Coefficients**: The notation above is called a multinomial coefficient

&nbsp;

### Combinations

**Definition - Combinations**: The total number of ways to create a $k$-element subset from $[n] = \{1, 2, \ldots, n\}$ is denoted
$${n \choose k} = \frac{n!}{k!(n-k)!} = \frac{P(n, k)}{k!}$$

- **Note**: the definition comes from $n!$ total possible distinct permutations of which we can permute a $k$-element subset $k!$ ways

&nbsp;

**Example**: There are $5$ cats, $5$ dogs, and $4$ mice. $3$ are chosen at once

- How many total number of ways  to get $2$ cats, $1$ dog?

  $\displaystyle {5 \choose 2} {5  \choose 1}$. This comes from choosing $2$ cats from $5$ cats, and then choosing $1$ dog from $5$ dogs

- How many total ways to get at least $1$ cat?

  $\displaystyle {14 \choose 3} - {9 \choose 3}$. This comes from subtracting the possible groupings with no cats from the total number of possible groupings

  $\displaystyle = {5 \choose 1}{9 \choose 2} + {5 \choose 2}{9 \choose 1} + {5 \choose 3}$. This comes from enumerating over possible groupings with 1 cat and 2 other animals, 2 cats and 1 other animal, and 3 cats and no other animals

&nbsp;

**Binomial Theorem**: If $n$ is a positive integer then
$$(x+y)^n = \sum_{k=0}^{n}{n \choose k}x^k y^{n-k}$$
*Proof*: $(x+y)^n = (x+y) \cdots (x+y)$

The coefficients of $x^k y^{n-k}$ is the product of $n$ terms distributing from $k$ $x$-terms and $n-k$ $y$-terms

So out of the $n$ terms that are multiplied together, ${n \choose k}$ contribute the $x$-term, leaving $n-k$ unused terms for $y$

Thus we have
$${n \choose k}x^k {n-k \choose n-k}y^{n-k} = {n \choose k} x^k y^{n-k}$$

&nbsp;

**Multinomial Theorem**: For $n \in Z^+$, we have
$$(x_1 + \cdots + x_k)^n = \sum_{\substack{a_1 + \cdots + a_k = n \\ a_1, \ldots, a_k \geq 0}}^{}{n \choose a_1, a_2, \ldots, a_k} x_1^{a_1} \cdots x_k^{a_k}$$

*Proof*: $(x_1 + \cdots x_k)^n = (x_1 + \cdots + x_k) \cdots (x_1 + \cdots + x_k)$

The coefficients of $x_1^{a_1} \cdots x_k^{a_k}$ is the product of $n$ terms resulting from a permutation with repetition of $a_1, \ldots, a_k$

Thus there are $\displaystyle {n \choose a_1, \ldots, a_k}$ distinct ways of representing the exponents of $x_1, \ldots, x_k$

&nbsp;

**Worksheet Examples**:

1.

   - How many strictly increasing 6-digit numbers are there (first digit can be 0)

      Since the numbers are strictly increasing, they numbers must be distinct

      Furthermore, there is only one possible way ordering of these selected digits (in increasing order), so order "doesn't matter"

      Thus we can just count the ways to select 6 digits: $\boxed{\displaystyle {10 \choose 6}}$

   - What about when the first digit cannot be zero?

      Since $0$ can only appear as the first digit, this is identical to the first question, but restricted to $\{1, \ldots, 9\}$

      $\boxed{\displaystyle {9 \choose 6}}$ ways

&nbsp;

2. A quiz has 5 problems with 3 different answers each. How many ways can the quiz be completed?

    $\boxed{3^5}$ ways

&nbsp;

3.

   - How many rearrangements of MISSISSIPPI are there?

      $\boxed{\displaystyle {11 \choose 4, 4, 2, 1}}$

   - How many rearrangements do not have all S's together?

      Treat all S's as one unit $\implies \displaystyle {8 \choose 4, 2, 1, 1}$

      Thus there are $\boxed{\displaystyle {11 \choose 4, 4, 2, 1} - \displaystyle {8 \choose 4, 2, 1, 1}}$ rearrangements

&nbsp;

4. Suppose each digit in a 5-digit code can have any number zero to nine

   - How many 5-digit codes are there with no restrictions?

      $\boxed{10^5}$

   - How many 5-digit codes have distinct digits?

      $\boxed{P(10, 5)}$

   - How many codes begin and end with an even number?

      $\boxed{5 * 10^4 * 5}$

   - How many 5-digit codes use exactly 2 different numbers?

      $\displaystyle {5 \choose 2}$ ways to choose two digits

      $2^5$ ways to write a five digit number using these two digits. However, we need to subtract the 2 cases where they use the same digit five times

      Thus answer is $\boxed{\displaystyle {5 \choose 2} (2^5 - 2)}$

&nbsp;

5. Consider a standard 52 card deck with 13 ranks and 4 suits

   - Probability of getting a full house (triple of the same rank, pair of another rank)

      $\boxed{\displaystyle \frac{\displaystyle {13 \choose 1}\displaystyle {4 \choose 3}\displaystyle {12 \choose 1}\displaystyle {4 \choose 2}}{\displaystyle {52 \choose 5}}}$

   - Probability of getting 2 pairs of different ranks and a 5th card of a different rank

      $\boxed{\displaystyle \frac{\displaystyle {13 \choose 2} \displaystyle {4 \choose 2} \displaystyle {4 \choose 2} *44}{\displaystyle {52 \choose 5}}}$

      Logic is to choose 2 types of ranks AT THE SAME TIME and then choosing possible pairs from those ranks. Finally multiply by $44$ (the remaining number of possible cards for the 5th card)

      &nbsp;

      **Note**: the answer below is NOT correct but is added to show an easy mistake to make

      $\displaystyle \frac{\displaystyle {13 \choose 1}\displaystyle {4 \choose 2}\displaystyle {12 \choose 1}\displaystyle {4 \choose 2} * 44}{\displaystyle {52 \choose 5}}$ is WRONG because we need to consider duplicate pairs (e.g. QQ, KK and KK, QQ)

      This solution ends up overcounting since we can choose Queens then Kings versus Kings then Queens, which yields the same hand

&nbsp;

6. $15$ people want to buy pre-made sandwiches. There are 7 H sandwiches, 4 C sandwiches, and 4 P sandwiches. If each person gets 1 sandwich, how many ways can the sandwiches be distributed?

    $\boxed{\displaystyle {15 \choose 7, 4, 4}}$

&nbsp;

7. 10 people are sitting at a circular table. How many seating arrangements are there?

    $\displaystyle \frac{10!}{10} = \boxed{9!}$

## Counting in 2 Ways

Given an equation, we count combinatorially in 2 ways

**Example**: $\displaystyle {n \choose k} = \displaystyle {n-1 \choose k} + \displaystyle {n-1 \choose k-1}$

LHS: chooses a $k$-size subset from $[n]$

RHS: Partitions subsets into 2 cases, containing element $1$ or not containing $1$

- Containing $1$: Pick $k-1$ elements from the remaining $n-1$ elements $\displaystyle {n - 1 \choose k - 1}$
- Not containing $1$: Pick $k$ from $n-1$ elements $\displaystyle {n-1 \choose k}$

Thus we have $\displaystyle {n \choose k} = \displaystyle {n-1 \choose k} + \displaystyle {n-1 \choose k-1}$

&nbsp;

**Example**: $\displaystyle \sum_{k = 0}^n k\displaystyle {n \choose k} = n2^{n-1}$

RHS: Picks 1 element to be the leader ($n$ choices)

Then from the remaining $n-1$ people, pick a subset ($2^{n-1}$ ways)

LHS: Picks a group of size $k$ ($\displaystyle {n \choose k}$ ways) and then select a leader amongst them ($k$ possible choices)

Thus $\displaystyle \sum_{k = 0}^{n} k \displaystyle {n \choose k} = n 2^{n-1}$

&nbsp;

**Example**: $\displaystyle \sum_{i=1}^{n}i (n - i + 1) = \displaystyle {n + 2 \choose 3}$

LHS: Let $a, b, c$ be numbers with $a < b< c$ from $[n+2]$. Fix $b = i + 1$ (the $i$th $+ 1$ element). Then there are $i$ choices for the element $a$ and $(n+ 2) - (i + 1) = n - i + 1$ choices for the element $c$

Thus the total ways to create a 3-size subset $\{a,b,c\}$ from $[n+2]$ is $\displaystyle \sum_{i=1}^{n} i(n-i+1) = \displaystyle {n+2 \choose 3}$

RHS: Counts the number of subsets of size $3$ from $[n+2]$

&nbsp;

**Example**: $\displaystyle {2n \choose n} = \sum_{k=0}^{n} \displaystyle {n \choose k}^2$

LHS: Count the number of size $n$ subsets of $[2n]$

RHS: Can be written as $\displaystyle \displaystyle {n \choose k} \displaystyle {n \choose n-k}$

So choose $k$ people from a group of size $n$ and $n-k$ people from another group of size $n$

Thus $\displaystyle \displaystyle {n \choose k} \displaystyle {n \choose n-k} = \displaystyle {2n \choose n}$

## Pigeon Hole Principle

**Theorem - Pigeon Hole Principle**: If $n+1$ pigeons are placed into $n$ pigeonholes, then there is at least one pigeonhole with at least $2$ pigeons

**Theorem - Generalized Pigeon Hole Principle**: If $n$ pigeons are placed into $k$ holes, then at least one hole has

- At most $\displaystyle \lfloor \frac{n-1}{k} \rfloor$ pigeons (round down)
- At least $\displaystyle \lceil \frac{n}{k} \rceil$ pigeons (round up)
- **Note**: the statements above are equivalent

*Proof*: Suppose all holes have $\displaystyle \leq \lfloor \frac{n-1}{k} \rfloor$ pigeons

Then there are at most $\displaystyle k \lfloor \frac{n-1}{k} \rfloor \leq n - 1 < n$ pigeons total. Which is a contradiction

&nbsp;

**Example**: Prove that in a group of 40 people, at least 4 people have a same birthday in the same month

40 pigeons and 12 holes $\implies \lceil \frac{40}{12} \rceil = 4$. Thus by PHP, the statement holds

&nbsp;

**Example**: Prove that if 6 distinct numbers are chosen from $[9]$, then 2 numbers will sum to 10

6 pigeons and 5 holes $(\{(1, 9), \ldots, (5, 5)\} \implies \lceil \frac{6}{5}\rceil = 2$. Thus by PHP, 2 of the numbers belong to the same pair and sum to 10

&nbsp;

**Example**; An athlete wants to work out 45 hours over a 30-day month and will work out at least 1 hour each day. Prove that there is a period of consecutive days such that the cumulative hours he has worked out is exactly 14

Let $a_i$ be the total hours accumulated up to day $i$

This creates a strictly increasing sequence $a_1, a_2, \ldots, a_{30} = 45$ where each $a_i$ is distinct

Define a new sequence $b_i = a_i + 14$

This creates a strictly increasing sequence $b_1, b_2, \ldots, b_{30} = 59$ where each $b_i$ is distinct

Since $\{a_i\}_{i=1}^{30}$ is distinct and $\{b_i\}_{i=1}^{30}$ is distinct (only within their own respective sequence), we can have at most $60$ possible values, which we treat as pigeons

Furthermore, $b_i$ can take on any of 59 distinct values, which we treat as the holes

Thus by PHP, some $a_j = b_k = a_k + 14$

Thus from day $k+1$ to day $j$, the total number of hours worked out is 14

## Compositions and Set Partitions

**Definition - Weak Composition**: Take $a_1, \ldots a_k \geq 0$ such that $\displaystyle \sum_{i=1}^{k} a_i = n$. Then the ordered $k$-tuple ($a_1, \ldots, a_k)$ is a **weak composition** of $n$ into $k$ partitions

- **Note**: This can be seen as distributing $n$ unlabelled balls into $k$ labelled boxes

&nbsp;

**Theorem - Stars and Bars**: The number of weak compositions of $n$ into $k$ parts is $\displaystyle {n + k - 1 \choose k - 1}$

*Proof*:

Denote the $n$ objects as stars. We model a distribution as follows:

Place $k$ bars where stars to the right of each bar is how many stars the corresponding part contains

**Note**: we must begin with a bar. Thus the rest involves $n$ stars and $k -1$ bars

Thus we can choose $k-1$ from these $n + k-1$ objects, resulting in $\displaystyle {n + k - 1 \choose k-1}$

Each one of these combination generates a different weak composition

&nbsp;

**Example**: How many ways can we distribute \$100 to 5 people?

- Can also be rephrased as how many non-negative integer solutions are there to $x_1 + \cdots + x_5 = 100$

Using the Stars and Bars Theorem, we have $\displaystyle {100 + 5 - 1 \choose 5 - 1} = \displaystyle {104 \choose 4}$ ways

&nbsp;

**Example**: Suppose we want to choose 3 lollipop flavors from 5 orange, 4 strawberry, and 3 grapes. How many ways can we choose 3 lollipops?

Here we want $x_O + x_S + x_G = 3$ where $x_O, x_S, x_G \geq 0$

Thus $\displaystyle {3 + 3 -1 \choose 3 - 1}$

&nbsp;

**Definition - Compositions**: Same as weak compositions but with the restriction that each $x_i \geq 1$

We can derive this with the formula above but ensuring that each of the $k$ boxes starts with 1 star, and then we distribute the remaining $n-k$ stars in a weak composition fashion. Thus the number of compositions of $n$ into $k$ parts is
$$\displaystyle {n - k + k - 1 \choose k - 1} = \displaystyle {n - 1 \choose k - 1}$$

**Note**: This problem is placing unlabelled balls into labelled bins

&nbsp;

**Definition - Partition**: Let $X$ be a finite set and $A_1, \ldots, A_k$ be non-empty subsets of $X$. Then a **partition** of $X$, $\{A_1, \ldots, A_k\}$ satisfies

- $\displaystyle \bigcup_{i=1}^k A_i = X$
- Each $A_i, A_j$ are pairwise disjoint

**Note**: This problem can be stated as: for a given $k$, $X$ is partitioned into $k$ **blocks**

&nbsp;

**Example**: $\{\{1, 2, 4\}, \{3, 5\}, \{6\}\}$ is a partition of $[6]$

The first inner set here can be considered placing balls $1, 2, 4$ into its own (unlabelled) bin

&nbsp;

**Definition - Stirling Number of the 2nd Kind**: The number of partitions of $[n]$ into $k$ **blocks**, denoted $S(n, k)$

- $S(0, 0) = 1$ by convention
- $S(n, 0) = 0$ for $n \geq 1$ is a partition of $[6]$

&nbsp;

**Example**: Use counting arguments to compute $S(n, 2)$

For each ball, we decide if it either it goes into block 1 or block 2, resulting in $2^n$

However, we require that each block has $\geq 1$ elements. Thus we need to subtract by $2$ for the cases where block 1 has all balls or block 2 has all balls by $2$ for the cases where block 1 has all balls or block 2 has all balls

Finally, we need to divide by 2 since the order of the blocks doesn't matter

$\displaystyle \frac{2^n - 2}{2}$

&nbsp;

**Theorem**: For $n \geq k$, we have
$$S(n, k) = S(n-1, k-1) + kS(n-1, k)$$

*Proof*:

LHS: Counts the number of ways to partition $[n]$ into $k$ blocks

RHS looks at partitions where

- $\{1\}$ is in its own bin. Then we need to partition $[n-1]$ into $k-1$ bins, resulting in $S(n-1, k-1)$
- $\{1\}$ is in a bin with other elements. Then we need to partition $[n-1]$ into $k$ bins, and then choose a bin to place $\{1\}$ into, resulting in $kS(n-1, k)$

**Theorem**: $S(n, k) = \displaystyle \frac{1}{k!} \sum_{i = 0}^k (-1)^i \displaystyle {k \choose i} (k-i)^n$

*Proof*: will show later

&nbsp;

**Definition - Bell Number**: Total number of partitions of $[n]$, denoted $B(n) = \displaystyle \sum_{k=1}^{n} S(n, k)$

- **Note**: $B(0) = 1$ by convention

&nbsp;

**Example**: Take $n=3$. Then we have
$$\{\{1, 2, 3\}\}, \{\{1\},\{2\},\{3\}\}, \{\{1\}, \{2, 3\}\}, \{\{2, \{1, 3\}\}\}, \{\{3\} \{1, 2\}\}$$
Thus $B(3) = 5$

&nbsp;

**Theorem**: $B(n) = \displaystyle \sum_{i=1}^{n}\displaystyle {n-1 \choose i-1} B(n-i)$

*Proof*:

LHS: counts the total number of partitions of $[n]$

RHS:

- Fix the $n$th element and determine the number of subsets of size $i$ that contain this element: $\displaystyle {n-1 \choose i-1}$ ways
- Partition the remaining $n-i$ elements: $B(n-i)$ ways

Thus we see that $B(n) = \displaystyle \sum_{i=1}^{n}\displaystyle {n-1 \choose i-1} B(n-i)$


&nbsp;

**Example**: Consider $f: A \rightarrow B$ where $|A| = n$ and $|B| = k$ for $n \geq k$. What is the total number of surjective functions?

- Recall that $f$ is surjective if for $\forall b \in B$, there exists at least one $a \in A$ such that $f(a) = b$

This problem can be viewed as partitioning $A$ into $\{A_1, \ldots, A_k\}$ and determining how they map to $B$, where $A_i = \{a \in A \mid f(a) = i\}$

Clearly the number of ways to partition $[n]$ into $k$ parts is $S(n, k)$

However, we also need to consider the order of the boxes (since they determine which subsets map to which values of $B$). Thus we need to multiply by $k!$

Thus the final answer is $k! S(n, k)$

## Integer Partitions

**Definition - Partition of Integer $\mathbf{n}$**: Positive sequence of integers $a_1, \ldots, a_k$, with $a_1 \geq a_2 \geq \cdots \geq a_k$ such that
$$a_1 + a_2 + \cdots + a_k = n$$
Total number of such sequences is denoted $p(n)$

- **Note**: Observe that since the values are non-increasing, the order "doesn't matter" so we don't need to distinguish $1 + 3 = 4$ from $3 + 1 = 4$
- **Note**: By convention, we have $p(0) = 1$

&nbsp;

**Example**: Take $n = 4$. Then we have
$$4 = 3 + 1 = 2 + 2 = 2 + 1 + 1 = 1 + 1 + 1 + 1$$
Thus $p(4) = 5$

&nbsp;

**Definition - Ferrers Diagram**: Represents a partition $(a_1, \ldots, a_k)$ by taking a partial rectangular grid with $k$ rows whose rows contain $a_i$ dots, such that $a_1 \geq \cdots \geq a_k$

&nbsp;

**Example**:

$$\young(~~~~,~~~,~,~,~)$$

This corresponds to $4 + 3 + 1 + 1 + 1= 10$

&nbsp;

**Definition - Conjugate of a Partition**: Diagram created by reflecting a Ferrers Diagram along the diagonal

- **Note**: Can be see as replacing columns as rows and rows as columns

&nbsp;

**Example**: Conjugate of the previous example

$$\young(~~~~~,~~,~~,~~,~)$$

This corresponds to $5 + 2 + 2 + 1 = 10$

&nbsp;

**Theorem**: Let $P_1$ denote the number of partitions where $a_1 = a_2 \geq a_3 \geq \cdots \geq a_k$ (for unfixed $k$). Let $P_2$ be the number of partitions whose smallest part is at least $2$. Then
$$P_1 = P_2$$

*Proof*: $\implies$ Take a partition where $a_1 = a_2$. Then take it's conjugate.

$$\young(~~~~~,~~~~~,~~,~~,~) \quad \quad \young(~~~~~,~~~~,~~,~~,~~)$$

Clearly every part of the conjugate has length $\geq 2$

Adding more dots to the original diagram doesn't affect the minimal lengths of the conjugate

Thus the conjugate assures each row has at least 2 dots $\implies$ each part has at least size $2$

$\impliedby$ Given a partition with $a_k \geq 2$, the conjugate creates a partition with $2$ rows that are the largest and have the same size. Thus $a_1 = a_2$ in the conjugate

&nbsp;

**Example**: Show that the total number of partitions of $n$ containing a part of size $1$ is $p(n-1)$

$\implies$ Take partition $P$ of $n$ containing a part of size $1$

This part will be the bottom row. Deleting that row yields $p(n-1)$

$\impliedby$ Given a partition $P_2$ of $n-1$, add a dot to the bottom. This yields a partition of $n$ with a part of size $1$

&nbsp;

**Definition - $\mathbf{p_k(n)}$**: Number of partitions of $n$ into exactly $k$ parts

&nbsp;

**Theorem**: For $1 < k < n$
$$p_k(n) = p_{k-1}(n-1) + p_k(n-k)$$
*Proof*:

LHS: counts the number of partitions of $n$ into $k$ parts

RHS:

- Count the number of partitions such that there is a partition of size $1$: $p_{k-1}(n-1)$
- Count the number of partitions such that every part has size $\geq 1$: $p_k(n-k)$

**Note**: Each part must have size $\geq 1$ by definition

## Twelvefold Way

Goal is to distribute $n$ (labelled or unlabelled) balls into $k$ (labelled or unlabelled) bins, depending on if the bins

- Have no restriction
- Have at least 1 ball
- Have at most 1 ball

This results in 12 possible scenarios

1. **$\mathbf{n}$ Labelled Balls into $\mathbf{k}$ Labelled Bins**

    - No restrictions: For each ball, pick a bin to put it into $\implies k^n$
    - At least 1: Can be viewed as the number of surjective functions $\implies k! S(n, k)$
    - At most 1:
      - If $n > k \implies 0$
      - Otherwise $n \leq k$ and we pick $n$ bins in a specific order $\implies P(k, n)$

2. **$\mathbf{n}$ Unlabelled Balls into $\mathbf{k}$ Labelled Bins**

    - No restrictions: Weak composition $\implies \displaystyle {n+k-1 \choose k-1}$
    - At least 1: Composition $\implies \displaystyle {n-1 \choose k-1}$
    - At most 1:
      - If $n > k \implies 0$
      - Otherwise $n \leq k$ and we just need to choose $n$ bins to use $\implies \displaystyle {k \choose n}$

3. **$\mathbf{n}$ Labelled Balls into $\mathbf{k}$ Unlabelled Bins**

    - No restrictions: Need to count all possible partitions with $0$ to $k$ parts $\implies \displaystyle \sum_{i=1}^{k}S(n, i)$
      - **Note**: This is NOT Bell's Number since we might have $k < n$
    - At least 1: Partition $[n]$ into $k$ parts $\implies$ $S(n, k)$
    - At most 1:
      - If $n > k \implies 0$
      - Otherwise $n \leq k$ and the bins are indistinguishable $\implies 1$ way

4. **$\mathbf{n}$ Unlabelled Balls into $\mathbf{k}$ Unlabelled Bins**

    - No restrictions: need to count all possible partitions with $0$ to $k$ parts $\implies \displaystyle \sum_{i=1}^{k}p_i(n)$
    - At least 1: Partition $n$ into $k$ parts $\implies p_k(n)$
    - At most 1:
      - If $n > k \implies 0$
      - Otherwise $n \leq k$ and the bins are indistinguishable $\implies 1$ way

&nbsp;

**Definition - Multiset**: Set of elements such that elements may repeat

&nbsp;

**Example**: How many multisets of size $5$ can be created using $[7]$?

Weak compositions for $1, 2, \ldots, 7$ such that the number of balls in each bin totals up to $5 \implies \displaystyle {5+7-1 \choose 7-1}$

&nbsp;

**Example**: How many injective functions $f: [n] \rightarrow [k]$ are there?

$n$ labelled balls into $k$ labelled bins where each big gets at most $1 \implies P(k, n)$

&nbsp;

**Example**: $20$ kids split into $4$ study groups. $2$ brothers must be in the same group and $2$ sisters must be in the same group. What is the total number of ways to split the kids

Treat the brothers and sisters each as one unit then partition $[18]$ into $4$ bins $\implies S(18, 4)$

## Inclusion-Exclusion Principle

**Theorem**: Let $A_1, \ldots, A_n \subseteq X$ where $X$ is finite and each $A_i$ is non-empty. Also let

- $I \subseteq [n]$
- $\displaystyle A_I = \bigcap_{i \in I} A_i$ with $A_{\emptyset} = X$

Then
$$\big| \bigcup_{i=1}^n A_i \big| = |X| - \displaystyle \sum_{I \subseteq [n]}^{} (-1)^{|I|} |A_I|$$

&nbsp;

**Note**: By De Morgan's Law, this is equivalent to

$$\displaystyle \big| \bigcap_{i = 1}^n \bar{A_i} \big| = |X| - \sum_{I \subseteq [n]}^{}(-1)^{|I|}|A_I|$$

&nbsp;

**Example**: For $n = 2 \implies I = \emptyset, \{1\}, \{2\}, \{1, 2\}$

\begin{align*}
\big| \bigcup_{i = 1}^2 A_i| &= |X| - \big((-1)^0 |X| + (-1)^1 |A_1| + (-1)^1 |A_2| + (-1)^2 |A_{\{1, 2\}}|\big) \\
&= |A_1| + |A_2| - |A_1 \cap A_2|
\end{align*}

&nbsp;

**Example**: How many integer solutions satisfy
$$x_1 + x_2 + x_3 = 35 \quad \quad \text{for } 0 \leq x_1, x_2, x_3, \leq 15$$

Consider the problem where $X_1 \geq 16$. We can place $16$ balls into the first bin then perform weak composition. We now use the negation form of the theorem above

Let $X$ be the set of all weak compositions. Now define

- $A_1 = \{\text{ weak compositions } \mid x_1 \geq 16\}$
- $A_2 = \{\text{ weak compositions } \mid x_2 \geq 16\}$
- $A_3 = \{\text{ weak compositions } \mid x_3 \geq 16\}$

Now we see that

\begin{align*}
\big| \bar{A_1} \cap \bar{A_2} \cap \bar{A_3} \big| &= \sum_{I \subseteq [3]}^{} (-1)^{|I|} |A_I| \\
&= \underbrace{{35 + 3 - 1 \choose 3 - 1}}_{I = \emptyset} - \underbrace{{3 \choose 1} {35 - 16 + 3 - 1 \choose 3 - 1}}_{I = \{1\}, \{2\}, \{3\}} + \underbrace{{3 \choose 2} \displaystyle {35 - 32 + 3 - 1 \choose 3 - 1}}_{I = \{1, 2\} \{1, 3\}, \{2, 3\}} - \underbrace{{3 \choose 3}(0)}_{\text{impossible since } 48 > 35}
\end{align*}

&nbsp;

**Example**: Count the total number of surjective functions $f: [n] \rightarrow [k]$, where $n \geq k$

Let $X$ be all functions from $[n] \rightarrow [k]$ and let $A_i$ be the set of functions that DO NOT map to $i \in [k]$. Then the total number of surjective functions is

\begin{align*}
\big| \bigcap_{i = 1}^k \bar{A_i}| &= \sum_{I \subseteq [k]}^{}(-1)^{|I|} |A_i|  \\
&= \sum_{i = 0}^{k} \displaystyle {k \choose i} (-1)^i (k-i)^n  \quad \quad \text{out of k, choose a set of image points not mapped to}\\
&= k!S(n, k)
\end{align*}

&nbsp;

**Example**: Consider the Euler Totient Function
$$\phi(n) = \big| \{i \in Z^+ \mid 1 \leq i \leq n, \gcd(i, n) = 1\} \big|$$

Let $p_1^{e_1} p_2^{e_2} \cdots p_t^{e_t}$, for $e_1 \geq 1$ be the prime factorization

Let $A_i = \{a \in [n] \mid p_1 \mid a\}$. Then we see value of $\phi(n)$ is

- Note $|A_1| = \frac{n}{p_1} \quad \quad$ how many numbers in $[n]$ have $2$ as a factor
- Note $|A_{\{1, 2\}}| = \frac{n}{p_1p_2} \quad \quad$ how many numbers in $[n]$ have $2$ AND $3$ as factors

\begin{align*}
\big| \bigcap_{i = 1}^t \bar{A_i} \big| &= \sum_{I \subseteq [t]} (-1)^{|I|}|A_I| \\
&= \underbrace{n}_{I = \emptyset} - \big(\frac{n}{p_1} + \frac{n}{p_2} + \cdots + \frac{n}{p_t} \big) + \big(\frac{n}{p_1p_2} + \frac{n}{p_2p_3} + \cdots \big) - \big( \frac{n}{p_1 p_2 p_3} + \cdots \big) + \cdots \\
&= n (1 - \sum_{i=1}^{t} \frac{1}{p_i} + \sum_{1 \leq i \leq j \leq t}^{} \frac{1}{p_i p_j} - \sum_{1 \leq i \leq j \leq k}^{} \frac{1}{p_i p_j p_k}) \\
&= n(1 - \frac{1}{p_1}) (1 - \frac{1}{p_2}) \cdots (1 - \frac{1}{p_t}) \\
&= n \prod_{i=1}^t (1 - \frac{1}{p_i})
\end{align*}

&nbsp;

**Example**: How many ways to seat 20 couples in a circular, unlabelled table with 40 seats such that each significant other doesn't sit with each other

Let $A_i$ be the set of seatings where couple $1$ is sitting next to each other. Then we see

\begin{align*}
\big| \bigcap_{i = 1}^{20} \bar{A_i} \big| &= \sum_{I \subseteq [20]}^{}(-1)^{|I|} |A_I| \\
&= \sum_{i = 0}^{20} \underbrace{20 \choose i}_{\mathclap{\text{select couples}}}  (-1)^i \underbrace{\frac{(40 - i)!}{40 - i}}_{\text{glue couples}}  \overbrace{2^i}^{\mathclap{{\text{order of couples}}}}
\end{align*}

# Chapter 2

## Review of Power Series

**Definition - Formal Power Series**: For a sequence $\{a_n\}_{n \geq 0}$, the **Formal Power Series**
$$F(x) = \sum_{n = 0}^{\infty}a_n x^n$$
Is the **Ordinary Generating Function** of $\{a_n\}_{n \geq 0}$

&nbsp;

**Example**: Let $\{a_n\}$ be given by
$$\frac{1}{2!}, \frac{1}{3!}, \ldots$$
Then the generating function is
\begin{align*}
F(x) &= \frac{1}{2!} + \frac{1}{3!}x + \frac{1}{4!}x^2 + \cdots\\
&= \frac{1}{x^2}( \frac{1}{2!} x^2 + \frac{1}{3!}x^3 + \cdots )\\
&= \frac{1}{x^2} \sum_{n = 2}^{\infty} \frac{x^n}{n!} \\
&= \frac{1}{x^2}(e^x - x - 1)
\end{align*}

&nbsp;

Same principle came be applied to find a sequence $\{a_n\}_{n \geq 0}$ given an OGF $F(x)$

**Example**: Find the sequence $\{a_n\}$ corresponding to
$$F(x) = \sum_{n = 0}^{\infty}a_n x^n = \frac{-4x + 3}{(1-x)(1 -2x)}$$

Using partial fractions we see
$$\frac{A}{1-x} + \frac{B}{1-2x} = -4x + 3 = A(1-2x) + B(1-x) \implies A = 1, B = 2$$
Thus we see that
\begin{align*}
F(x) &= \frac{-4x + 3}{(1-x)(1-2x)} \\
&= \frac{1}{1-x} + \frac{2}{1- 2x}\\
&= \sum_{n=0}^{\infty}x^n + \underbrace{2\sum_{n=0}^{\infty}(2x)^n}_{\sum_{}^{} 2^{n+1}x^n}\\
&= \sum_{n=0}^{\infty} (1+2^{n+1})x^n
\end{align*}
Thus $\{a_n\}_{n \geq 0} = \{1 + 2^{n+1}\}$

&nbsp;

### OGF's and Recurrences

We can replace $a_n$ with recursions for OGFs $\sum a_n x^n$

**Example**: Consider codes of length $n$ using A, B, C, D

Let $a_n$ be the total codes containing an even number of A's

1. Find a recurrence for $a_n$ in terms of $a_{n-1}$

    $a_n = 3a_{n-1} + 4^{n-1} - a_{n-1}$

    This comes from

    - Code doesn't end in A $\implies a_n = 3a_{n-1}$ (there are $3$ possible letters for the last letter)
    - Code ends in A $\implies 4n^{n-1} - a_{n-1}$ (All codes of length $n-1$ minus codes of length $n-1$ with an even number of A)

2. Find the OGF for $\{a_n\}$

\begin{align*}
f(x) &= \sum_{n=0}^{\infty}a_n x^n = \underbrace{1}_{a_0} + \sum_{n=1}^{\infty}a_n x^n \\
&= 1 + \sum_{n=1}^{\infty}(2a_{n-1} + 4^{n-1})x^n \\
&= 1 + \sum_{n=1}^{\infty}2a_{n-1} x^n + \sum_{n=1}^{\infty}4^{n-1}x^n \\
&= 1 + 2x \underbrace{\sum_{n=1}^{\infty} a_{n-1} x^{n-1}}_{f(x)} + x\underbrace{\sum_{n=1}^{\infty}(4x)^{n-1}}_{\text{geometric sum}}\\
&= 1 + 2x(f(x) + x(\frac{1}{1-4x}))\\
\end{align*}

&nbsp; &nbsp; &nbsp; &nbsp; Thus $\displaystyle f(x) = \frac{1}{1-2x} + \frac{x}{(1-2x)(1-4x)}$

3. Find the closed form of $a_n$

    By partial fractions, we have

\begin{align*}
f(x) &= \frac{1}{1-2x} + \frac{-1}{2(1-2x)} + \frac{1}{2(1-4x)}\\
&= \frac{1}{2}(\sum_{n = 0}^{\infty} (2x)^n) + \frac{1}{2} \sum_{n=0}^{\infty} (4x)^n\\
&= \sum_{n=0}^{\infty}\underbrace{(\frac{2^n}{2} + \frac{4^n}{2})}_{a_n}x^n
\end{align*}

&nbsp; &nbsp; &nbsp; &nbsp; Thus we have $\{a_n\} = \displaystyle \{2^{n-1} + \frac{4^n}{2}\}$

## OGFs and Counting

Using $\displaystyle \frac{1}{1-x} = \sum_{n=0}^{\infty} x^n$, we can differentiate to get

\begin{align*}
\frac{1}{(1-x)^2} &= \sum_{n=1}^{\infty}n x^{n-1}  = 1 + 2x + \cdots = \sum_{n= 0}^{\infty}(n+1)x^n \\
\frac{2}{(1-x)^3} &= \sum_{n=2}^{\infty}n(n-1) x^{n-2}  = 1 + 2x + \cdots = \sum_{n= 0}^{\infty}(n+2)(n+1)x^n \\
&\cdots \\
\frac{m!}{(1-x)^{m+1}} &= \sum_{n=0}^{\infty} \underbrace{(n+m)(n+m-1) \cdots (n+1)}_{(n+m)_m} x^n = \sum_{n=0}^{\infty} \frac{(n+m)!}{n!}x^n\\
\end{align*}

Thus we have
$$\frac{1}{(1-x)^{m+1}} = \sum_{n=0}^{\infty} \frac{(n+m)!}{n!m!}x^n = \sum_{n= 0}^{\infty} \displaystyle {n+m \choose m}x^n$$

For a fixed $m$, we have
$$\frac{1}{(1-x)^{m+1}} \iff \{a_n\} \quad \quad a_n = \displaystyle {n+m \choose m}$$
Which is the OGF for weak compositions into $m+1$ bins. However, we can now interpret
$$\frac{1}{(1-x)^k} = \underbrace{(\frac{1}{1-x})(\frac{1}{1-x}) \cdots}_{\text{apply geometric series k times}} = (1 + x + x^2 + \cdots + \cdots) (1 + x + x^2 + \cdots + \cdots) \cdots$$
Consider the question of getting coefficients of $x^7$. This corresponds to the weak compositions of $7$ unlabelled balls into $k$ bins

However, now the chosen exponents correspond to the bin sizes. Thus we see that the OGF for weak compositions is
$$F(x) = \frac{1}{(1-x)^k} = \sum_{n=0}^{\infty}a_n x^n = \sum_{n=0}^{\infty}\displaystyle {n+k-1 \choose k-1}x^n$$
To obtain coefficients of $a_n$, contributions come from $x^{n_1}$ from group 1, $x^{n_2}$ from group 2, etc. such that
$$x^{n_1} x^{n_2} \cdots x^{n_k} = x^n \implies n_1 + n_2 + \cdots + n_k = n \quad \quad n_i \geq 0$$

&nbsp;

**Example**: 5 apple, 4 pear, and 6 orange lollipops. Find the OGF that would yield the total ways to get 5 lollipops. State the term that we want
$$F(x) = \underbrace{(1 + x + \cdots+ x^5)}_{\text{apples}}\underbrace{(1 + x + x^4)}_{\text{pears}} \underbrace{(1 + x + \cdots + x^6)}_{\text{oranges}}$$

We want coefficients of $x^5$ in $F(x)$. Here the OGF is
$$\frac{1}{(1-x)^k} \longleftrightarrow \{\displaystyle {n+k-1 \choose k-1}\}$$

&nbsp;

**Theorem**: Let $k$ be a fixed positive integer. Then the OGF for Stirling Numbers $S(n, k)$ is
$$F_k(x) = \sum_{n=0}^{\infty}a_nx^n = \frac{x^k}{(1-x)(1-2x) \cdots (1-kx)}$$

*Proof*: Note that
$$S(0, 0) = 1 \quad \quad S(n, 0) = 0 \quad \quad S(0, k) = 0$$
Also recall the recurrence
$$S(n, k) = S(n-1, k-1) + kS(n -1, k)$$
Then we see that
\begin{align*}
F_k(x) = \sum_{n=0}^{\infty}S(n, k)x^n &= 0 + \sum_{n=1}^{\infty}\Big(S(n-1, k-1) + kS(n-1, k)\Big)x^n \\
&= \Big(x\sum_{n=1}^{\infty}S(n-1, k-1)x^{n-1}\Big) + \Big( kx \sum_{n=1}^{\infty}S(n-1, k) x^{n-1}\Big) \\
&= xF_{k-1}(x) + kxF_k(x)
\end{align*}
Thus $\displaystyle F_k(x) = \frac{xF_{k-1}(x)}{(1-kx)}$
Finally, applying the above equation recursively, we see that
\begin{align*}
F_k(x) = \frac{x}{1-kx} \frac{x}{1-(k-1)x} F_{k-2} &= \cdots \\
&= \frac{x^k}{(1-x)(1-2x) \cdots (1-kx)}
\end{align*}

Thus the OGF is
$$\prod_{t=1}^k \frac{x}{(1-tx)} \longleftrightarrow \{S(n, k)\}$$

&nbsp;

**Theorem**: Let $p(n)$ denote the total partitions of an integer $n$. Then the OGF for $p(n)$ is
$$F(x) = \sum_{n=0}^{\infty}p(n)x^n = \frac{1}{(1-x)(1-x^2) \cdots} = \prod_{k=1}^\infty \frac{1}{1-x^k}$$
*Proof*:
\begin{align*}
F(x) &= \frac{1}{1-x} \frac{1}{1-x^2}\frac{1}{1-x^3} \cdots \\ \\
&= \underbrace{(1 + x + x^2 + x^3 + \cdots)}_{\text{how many 1's}} \underbrace{(1 + x^2 + x^4 + x^6 + \cdots)}_{\text{how many 2's}}\underbrace{(1 + x^3 + x^6 + x^9 + \cdots)}_{\text{how many 3's}} \cdots\\ \\
&= \prod_{k=1}^\infty (1 + x^k + x^{2k} + \cdots)
\end{align*}

&nbsp;

Consider the question: how many combinations of $x^n$?

For $x^{m(k) * k}$, $m(k)$ is the total number of k's in the partition. For example, $m(1)$ is the total 1's in the partition

All possible contributions of $x^n$ is exactly the total partitions of integer $n$

&nbsp;

**Example**: Given an unlimited number of pennies, nickels, dimes, quarters, and half dollars, find the OGF that would count the total ways to make $\$1$. What is the coefficient?

We want coefficients of $x^{100}$ where
\begin{align*}
F(x) = \underbrace{(1 + x + \cdots + x^{100})}_{\text{number of pennies}} \underbrace{(1 + x^5 + \cdots + x^{100})}_{\text{number of nickels}}\underbrace{(1 + x^{10} + \cdots + x^{100})}_{\text{number of dimes}}\underbrace{(1 + x^{25} + \cdots + x^{100})}_{\text{number of quarters}}\underbrace{(1 + x^{50} + x^{100})}_{\text{number of half dollars}} \\
\end{align*}

Expanding (done on computer) yields $292x^{100} \implies 292$ ways

&nbsp;

**Theorem**: Total ways to partition $n$ into distinct parts equals the total ways to partition $n$ into odd sized parts

*Prof*: Distinct parts OGF is
\begin{align*}
F(x) &= (1 + x) (1 + x^2) + \cdots \quad \quad \text{this comes from each number only appears once}\\
&= (\frac{1 - x^2}{1 - x})(\frac{1 - x^4}{1 - x^2}) \cdots \\
&= (\frac{1}{1-x})(\frac{1}{1-x^3})(\frac{1}{1-x^5}) \cdots \\
&= (1 + x + x^2 + \cdots) (1 + x^3 + x^6 + \cdots)
\end{align*}
From above, we see that the even terms get cancelled and we are only left with the odd terms

Thus number of ways to partition $n$ into distinct parts equals the total number of ways to partition $n$ into odd sized parts

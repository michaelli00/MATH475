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

\newpage

# Chapter 1

## The Basics - Permutations, Combinations, and General Counting

### Permutation

**Definition - Permutation**: A **permutation** of an $n$-element set is an arrangement of the elements in a specific order

- $k$-permutation: arrangement of $k$ elements from the set
- The total number of $k$-permutation of an $n$-element set is
$$P(n, k) = \frac{n!}{(n-k)!} = n(n-1) \cdots (n-k + 1)$$

&nbsp;

**Example**: 10 people can run for office for a committee with a President, Vice President, Treasurer. The total number of possible committees is $P(10, 3)$

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

**Theorem 1**: Suppose object $1$ occurs $a_1$ times, object $2$ occurs $a_2$ times, $\ldots$, object $k$ occurs $a_k$ times. Furthermore, suppose $a_1 + \cdots + a_k = n$

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

   - How many codes begin and end with an even number?


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

&nbsp;

**Example**: How many ways can we distribute \$100 to 5 people?

- Can also be rephrased as how many non-negative integer solutions are there to $x_1 + \cdots + x_5 = 100$

Using the Stars and Bars Theorem, we have $\displaystyle {100 + 5 - 1 \choose 5 - 1} = \displaystyle {104 \choose 4}$ ways

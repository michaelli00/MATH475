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

<!-- # Pigeon-Hole Principle -->

<!-- ## Introduction -->

<!-- **Theorem 1.1 (Pigeon-Hole Principle)**: Let $n, k \in Z^+$ with $n > k$. Suppose we have $n$ balls to place into $k$ boxes. Then at least one box will have $\geq 2$ balls -->

<!-- *Proof by Contradiction*: Assume no boxes has $\geq 2$ balls. Then each box either has $0$ or $1$ balls in it. Let $m$ be the number of boxes with $0$ balls and $k-m$ be the number of boxes with $1$ ball. -->

<!-- This creates a contradiction since we would have $k -m < n$ balls in boxes -->

<!-- **Example**: There is an element in the sequence $7, 77, 777, \ldots$ that is divisible by $2003$ -->

<!-- **Solution**: We show that one of the first $2003$ elements is divisible by $2003$. --> 

<!-- Assume by contradiction this is false and take the first $2003$ elements of this sequence and divide by $2003$ -->

<!-- Since none of them are divisible by $2003$, they will all have a remainder $\in \{1, \ldots, 2002\}$ -->

<!-- Since we are testing $2003$ numbers and there are only $2002$ possible remainders, $2$ elements, $a_i$ and $a_j$, must have the same remainder by PHP -->

<!-- Thus $2003 \mid a_j - a_i$. In particular, $a_j - a_i$ has $j-1$ digits equal to $7$ and $i$ digits equal to $0$ -->

<!-- Thus $a_j - a_i = a_{j-i} \cdot 10^{i} \implies 2003 \mid a_{j-1}$ since $2003 \nmid 10^{i}$ -->

<!-- **Example**: Consider a chess tournament with $n$ players where any $2$ players must play a game against each other. Then at any point $2$ players have finished the same number of games -->

<!-- **Solution**: Consider the PHP scenario: Let balls be the number of players and boxes be the number of games finished -->

<!-- Note that if a player has $n-1$ games completed, then no player can have $0$ games played -->

<!-- Thus only $n-1$ boxes are used at any point, and by PHP, $2$ players have finished the same number of games at any time -->

# Introduction

**Combinatorics** is concerned with the existence, enumeration, analysis, and optimization of discrete structures (finite sets)

Combinatorics problems can be generalized into 2 types of problems

- *Existence of arrangement*: can we arrange objects of a set such that certain conditions are met?
- *Enumeration/classification of arrangements*: if a special arrangement is possible, there may be several ways of achieving it. Classify them into types

# Permutations and Combinations

## Basic Counting Principles

**Partition**: Let $S$ be a set. A **partition** of $S$ is a collection of subsets $S_1, \ldots, S_m$ of $S$ such that each element of $S$ is in exactly one subset
$$S = S_1 \cup S_2 \cup \cdots \cup S_m$$

Where $S_1, \ldots, S_m$ are pairwise disjoint

**Addition Principle**: Suppose $S$ is partitioned into pairwise disjoint parts $S_1, \ldots, S_m$. Then the number of elements in $S$ is determined by the number of elements in each part
$$|S| = |S_1| + |S_2| + \cdots + |S_m|$$

**Multiplication Principle**: Let $S$ be a set of ordered pairs $(a, b)$ where $a$ comes from a set of size $p$ and for each $a$, there are $q$ choices for $b$. Then
$$|S| = p \times q$$

This results from the additional principle. Let $a_1, \ldots, a_p$ be different choices for $a$ and are each in a partition $S_i$ of $S$. Then
$$|S_i| = q \implies |S| = |S_1| + \cdots + |S_p| = p \times q$$
This can be generalized for ordered pairs with $\geq 2$ elements

- **Example**: Determine the number of positive factors of $3^4 * 5^2 * 11^7 * 13^8$

    **Solution**: number of factors is $5 * 3 * 8 * 9 = 1080$

**Subtraction Principle**: Let $A \subset U$ and $\bar{A} = U \setminus A$ be the complement of $A$ in $U$. Then
$$|A| = |U| - |\bar{A}|$$

- **Example**: Suppose passwords compose of $6$ symbols from $\{0, \ldots, 9, a, \ldots, z\}$. How many passwords have repeated symbols?

    **Solution**: $|U| = 36^6$ and $|\bar{A}| = 36 * 35 * 34 * 33 * 32 * 31 \implies |A| = |U| - |\bar{A}| = 774, 372, 096$

**Division Principle**: Let $S$ be a finite set partitioned into $k$ parts such that each part has the same number of elements. Then
$$k = \frac{A}{\# \text{ of elements per part}}$$

- **Example**: Suppose we have $740$ pigeons and pigeonholes of size $5$. How many pigeonholes do we have?

    **Solution**: $\frac{740}{5} = 148$ pigeonholes

Counting problems can be classified into 2 types of problems

- **Permutation**: count the number of ordered arrangements
  - Without repeating any object
  - With repetition permitted
- **Combination**: count the number of unordered arrangements
  - Without repeating any object
  - With repetition permitted

**Example**: Find the number of odd numbers between $1000, 9999$ that have distinct digits

**Solution**: unit digit restricted to $\{1, 3, 5, 7, 9\}$, tens and hundreds place restricted to $\{0, \ldots, 9\}$, thousands place restricted to $\{1, \ldots, 9\}$

We quantify units, thousands, hundreds, tens: $5 * 8 * 8 * 7 = 2240$

- **NOTE**: we start with the most restrictive choice first (unit digit)

**Example**: Number of integers between $0$ and $10, 000$ with one digit equal to $5$

**Solution**: First partition $S$ into

- $S_1$: set of one digits numbers. $|S_1| = 5$
- $S_2$: set of two digit numbers. $|S_2| = 8 + 9 = 17$
- $S_3$: set of three digit numbers. $|S_3| = 8*9 + 8*9 + 9*9 = 225$
- $S_4$: set of four digit numbers. $|S_4| = 8 *9 *9 + 8*9*9 + 8*9*9 + 9*9*9 = 2673$

Thus $|S| = 2916$

## Permutation of Sets

Let $r$ be a positive integer. A **r-permutation** of a set $S$ with $n$ elements is an ordered arrangements of $r$ of the $n$ elements

- If $r > n$ then $P(n, r) = 0$
- $P(n, 1) = n$
- $P(n, 0) = 1$

**Theorem 2.2.1**: $P(n, r) = n * (n-1) * \cdots * (n - r + 1)$

**Proof**: We can choose the first item $n$ ways, the second item $n-1$ ways, $\ldots$, the $rth$ item $n - (r - 1)$ ways. 

By multiplication principle we get $P(n, r) = n * (n-1) * \cdots * (n- r + 1)$

**Example**: the number of ways to order $26$ letters such that no $2$ vowels occur consecutively

**Solution**: There are $21$ consonants $\implies 21!$ permutations of consonants

Vowels must be in $5$ of the spaces before, between, or after consonants $P(22, 5) = \frac{22!}{17!}$

Thus number of arrangements is $21! * \frac{22!}{17!}$

**Example**: How many $7$ digit numbers are there with distinct digits and don't have $5, 6$ appearing consecutively in either order

**Solution 1**: We count various partitions and sum their orders together

- $S_1$: neither $5, 6$ appear $\implies P(7, 7) = 7! = 5040$
- $S_2$: $5$ appears but not $6$ $\implies 7 * P(7, 6) = 7 * 7! = 35280$
- $S_3$: $5$ appears but not $5$ $\implies 7 * P(7, 6) = 7 * 7! = 35280$
- $S_4$: Both $5, 6$ appear

  - First digit is $5$ and second digit is not $6 \implies 5 * P(7, 5) = 126000$
  - Last digit is $5$ and second to last digit is not $6 \implies 5 * P(7, 5) = 126000$
  - $5$ occupies one of the interior $5$ places so $6$ can appear only in $4$ places $\implies 5 *4 * P(7, 5) = 50400$

Thus answer is $151200$

**Solution 2**: Consider the set of all digits $P(9, 7) = 181400$

Let $\bar{S}$ be the complement of the set we need.

- There are $6$ ways to position $5$ followed by $6$
- There are $6$ ways to position $6$ followed by $5$

Thus $|\bar{S}| = 2 * 6 * P(7, 5) = 30240$

Thus $|S| = |U| - |\bar{S}| = 181400 - 30240 = 151200$


**Theorem 2.2.2**: Number of circular r-permuations is
$$\frac{P(n, r)}{r} = \frac{n!}{r(n-r)!}$$

**Proof**: Set of linear r-permutations can be partitioned into parts such that 2 linear r-permutations correspond to the same r-permutation if and only if they are in the same part (these are of size $r$)

This means that the number of circular permuations is the number of parts

Thus by the division principle, the number circular permutations is $\frac{P(n, r)}{r}$

**Note**: one way to view circular permutations of $A, B, C, D, E, F$ is to fix $A$ and identify the linear permutations of $B, c, d, e, f$

- In this case, there are $5!$ circular permutations of $A, B, C, D, E, F$

**Example**: Consider seating 10 people around a round table but 2 people don't want to sit next to each other. How many seating arrangements are there?

**Solution 1**: Let $P_1, \ldots, P_{10}$ be the people and suppose $P_1, P_2$ don't want to sit next to each other

Consider seating arrangements for $9$ people: $X, P_3, \ldots, P_{10}$. There are $8!$ arrangements for this

If we replace $X$ with $P_1, P_2$ or $P_2, P_1$ we get the complement of the set we want

Thus the number of seating arrangements is $9! - 2*8! = 282240$

**Solution 2**: Let $P_1$ be the head of the table. $P_2$ cannot be next to $P_1$

Thus there are $8$ choices for $P_1$'s left and $7$ choices for $P_1$'s right

Finally we permute the remaining $7$ seats

Thus answer is $8 * 7 * 7! = 282240$

## Combinations of Sets

**Combination**: unordered selection of elements in $S$

- If $r > n$, ${n \choose r} = 0$
- If $r > 0$, ${0 \choose r} = 0$
- ${n \choose 0} = {0 \choose 0} = 1$
- ${n \choose 1} = n$
- ${n \choose n} = 1$

**Theorem 2.3.1**: For $0 \leq r \leq$
$$P(n, r) = r! {n \choose r}, \quad \quad {n \choose r} = \frac{n!}{r!(n-r)!}$$

**Proof**: Each r-permutation of $S$ arises exactly one way as a result of

- Choose $r$ elements of $S$
- Ordering these elements

First step is done by ${n \choose r}$

Second step is done by $P(r, r) = r!$

Thus $P(n, r) = r! {n \choose r} \implies {n \choose r} = \frac{n!}{r!(n-r)!}$

**Example**: $15$ people are enrolled in math class but only $12$ students attend class per day. If there are $25$ seat, how many ways might the instructor see the students?

**Solution**: ${15 \choose 12} = \frac{15!}{12!3!} = 455$ combinations of $12$ students attending class

For $12$ students and $25$ seats, there are $P(25, 12)$ ways of seating themselves

Thus there are ${15 \choose 12} P(25, 12)$ ways the instructor might see $12$ students

**Example**: How many $8$ letter words are there if each word has $3, 4,$ or $5$ vowels

**Solution**: 

- $|S_3| = {8 \choose 3} *5^3 * 21^5$
- $|S_4| = {8 \choose 4} *5^4 * 21^4$
- $|S_5| = {8 \choose 5} *5^5 * 21^3$

Thus $|S| = |S_3| + |S_4| + |S_5|$

**Corollary 2.3.2**: For $0 \leq r \leq n$
$${n \choose r} = {n \choose n - r}$$

**Theorem 2.3.3 (Pascal's Formula)**: for integers $n, k$ such that $1 \leq k \leq n - 1$
$${n \choose k} = {n \choose k} + {n - 1  \choose k - 1}$$

**Proof**: Let $|S| = n$ and take $x \in S$

Consider $S \setminus \{x\}$ and partition set $X$ of k-subsets of $S$ where into

- $A$: k-subsets without $x$. This has size ${n-1 \choose k}$
- $B$: k-subsets with $x$. This has size ${n - 1 \choose k - 1}$

Thus $|X| = {n \choose k} = |A| + |B| = {n \choose k} + {n - 1  \choose k - 1}$

**Theorem 2.3.4**: For $n \geq 0$
$${n \choose 0} + {n \choose 1} + \cdots + {n \choose n} = 2^n$$

**Proof**: We use double counting. First, ${n \choose 0} + {n \choose 1} + \cdots + {n \choose n}$ is the number of subsets of $S$

Secondly, for a subset of $S$, we need to decide if $x_1, x_2, \ldots, x_n$ goes into the subset or not. Thus there are $2^n$ to form a subset of $S$

Thus the Theorem holds since we counted values on both sides of the equation

**Example**: Show that the number of 2-subsets of $\{1, 2, \ldots, n\}$ is ${n \choose 2}$

**Solution**: Partition the 2-subsets according to the largest largest integer they contain

The number of 2-subsets in which $i$ is the largest integer is $i-1$

Thus we must have $0 + 1 + \cdots + (n-1) = {n \choose 2} = \frac{n(n-1)}{2}$

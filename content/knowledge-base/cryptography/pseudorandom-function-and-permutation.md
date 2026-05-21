---
# prettier-ignore
date: 2026-05-21
title: Pseudorandom Function and Permutation
weight: 10
---

Let $\text{Func}_n$ be all functions mapping $\{0,1\}^n$ to $\{0,1\}^n$, and $\left| \text{Func}_n \right| = 2^{n \cdot 2^n}$.

Then, a random function $f \in \text{Func}_n$ is chosen uniformly.

## Keyed Functions

Let $F: \{0,1\}^* \times \{0,1\}^* \rightarrow \{0,1\}^*$ be an efficient, deterministic algorithm, and define $F_k = F(k, x)$, then the first input $k$ is called the key.

Then, choose a uniform $k \in \{0,1\}^n$ is equivalent to choosing the function $F_k: \{0,1\}^n \rightarrow \{0,1\}^n$, thus, the algorithm $F$ defines a distribution over functions in $\text{Func}_n$.

Therefore, $F_{k \in \{0,1\}^n} \subset \text{Func}_n$, and the number of $F_{k \in \{0,1\}^n}$ is at most $2^n$.

## Pseudorandom Functions Definition (PRFs)

The formal definition of pseudorandom functions is:

$F$ is a pseudorandom function if $F_k$, for uniform key $k \in \{0,1\}^n$, is indistinguishable from a uniform function $f \in \text{Func}_n$.

## Pseudorandom Permutations (PRPs)

Let $f \in \text{Func}_n$, $f$ is a permutation if it is a bijection, which means $f^{-1}$ exists.

Let $\text{Perm}_n \subset \text{Func}_n$ be the set of permutations.

$$
\left| \text{Perm}_n \right| = 2^n \times (2^n - 1) \times (2^n - 2) \times \dots \times 1 = (2^n)!
$$

### Keyed Permutation

Let $F$ be a length-preserving, keyed function, then $F$ is a keyed permutation if $F_k$ is a permutation for every $k$, and $F^{-1}$ is efficiently computable.

$F$ is a strong pseudorandom permutation if $F_k$ for uniform key $k \in \{0,1\}^n$, is indistinguishable from a uniform permutation $f \subset \text{Perm}_n$.

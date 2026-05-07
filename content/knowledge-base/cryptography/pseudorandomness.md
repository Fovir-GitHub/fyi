---
# prettier-ignore
date: 2026-05-07
title: Pseudorandomness
weight: 8
---

## Definition

$S$ is a set of binary strings of length $\ell$, then

- $G$ is some probability distribution on $S$
- $U$ is uniform probability distribution on $S$

Then $G$ is called pseudorandom if a string drawn according to $G$ is indistinguishable from a string drawn according to $U$ to an PPT adversary.

## Pseudorandom Generator

Let $G$ be a deterministic polynomial-time algorithm such that for any $n$ and any input $s \in \{0,1\}^n$, the result $G(s)$ is a string of length $\ell(n)$. $G$ is a pseudorandom generator if:

- $\forall n, \ell(n) > n$
- The output of $G$ looks like a uniform string to any PPT observer

Formal definition:

$G$ is a pseudorandom generator, if $\forall \mathcal{A}, \exists \varepsilon$ such that

$$
\left| Pr[\mathcal{A}(U) = 1] - Pr[\mathcal{A}(G(s))] \right| \le \varepsilon(n)
$$

Where $\mathcal{A}$ is PPT adversaries, $\varepsilon$ is a negligible function.

## EAV-Security from a Pseudorandom Generator

Let $G$ be a pseudorandom generator with expansion factor $\ell(n)$, then define a fixed-length private-key encryption scheme $\Pi$ for messages of length $\ell(n)$ as:

- $Gen$: on input $1^n$, choose uniform key $k \in \{0,1\}^n$ and output it as the key
- $Enc$: on input key $k \in \{0,1\}^n$ and a message $m \in \{0,1\}^{\ell(n)}$, output the ciphertext
  $$
  c: G(k) \oplus m
  $$
- $Dec$: on input key $k \in \{0,1\}^n$ and a ciphertext $c \in \{0,1\}^{\ell(n)}$, output the message
  $$
  c: G(k) \oplus c
  $$

If $G$ is a pseudorandom generator, then $\Pi$ is an EAV-Secure, fixed-length private-key encryption scheme for messages of length $\ell(n)$

## Pseudorandom Number Generators (PRNGs)

PRNGs often use deterministic algorithmic techniques to create random like numbers.

## Linear Feedback Shift Registers (LFSR) as PRNGs

Feed back function is linear over $\mathbb{F}_2$

### Period

The maximum period for an $n$-bit register is $2^n - 1$

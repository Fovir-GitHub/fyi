---
# prettier-ignore
date: 2026-05-03
title: Computational Security
description: Note of computational security.
weight: 7
---

## Perfect Secrecy vs. Computational Security

Perfect secrecy emphasizes that no plaintext information is leaked, although eavesdroppers have unlimited computational power.

Computational security allows a scheme to leak information with tiny probability to eavesdroppers with bounded computing resources/running time.

## Complexity Theory

Complexity theory provides a methodology for analyzing the computational complexity of different cryptographic techniques and algorithms.

## Concrete Security

$(t,\varepsilon)$-indistinguishability:

- Security may fail with probability $\le \varepsilon$
- Restrict attention to attackers running in time $\le t$, or $t$ CPU cycles.

If $\Pi$ is $(t, \varepsilon)$-indistinguishable for all attackers $\mathcal{A}$ running in time at most $t$, then

$$
Pr[\text{PrivK}_{\mathcal{A},\Pi} = 1] \le \frac{1}{2} + \varepsilon
$$

> $(\infty,0)$-indistinguishability = perfect indistinguishability

### Limitation

- Sensitive to exact computational model
- Precise concrete guarantees are difficult to provide
- One must be careful in interpreting concrete-security claims

## Asymptotic Security

Introduce security parameter $n$.

And $t$ is the probabilistic polynomial time (PPT) in $n$.

$\varepsilon$ is a negligible function in $n$.

### Computational Indistinguishability

- Security may fail with probability negligible in $n$
- Restrict attention to attackers running in time polynomial in $n$

## Comparison

**Concrete Security:** A scheme is $(t,\varepsilon)$-secure if for any adversary running for time at most $t$ succeeds in breaking the scheme with probability at most $\varepsilon$

**Asymptotic Security:** A scheme is secure if any PPT adversary succeeds in breaking the scheme with probability at most negligible.

## Another Definition of Encryption

A private-key encryption scheme is defined by three PPT algorithms ($Gen$, $Enc$, $Dec$):

- $Gen$ takes as input $1^n$, and outputs $k$ (assume $\left| k \right| \ge n$)
- $Enc$ takes as input a key $k$ and message $m \in \{0,1\}^{*}$, and outputs ciphertext $c$
  $$
  c \gets Enc_k{(m)}
  $$
- $Dec$ takes key $k$ and ciphertext $c$ as input, and outputs a message $m$ or error.

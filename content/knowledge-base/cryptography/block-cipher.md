---
# prettier-ignore
date: 2026-05-21
title: Block Cipher
weight: 11
description: Note of block cipher.
---

## Definition

A block cipher is an efficient, keyed permutation $F: \{0,1\}^n \times \{0,1\}^\ell \rightarrow \{0,1\}^\ell$, where $n$ defines the key length, and $\ell$ defines the block length.

## Attack Model

Although a block cipher is not an encryption scheme, some terminology used is the same.

- **Known-plaintext Attack:** Attacker given $\{(x,F_k(x))\}$ for arbitrary $x$
- **Chosen-plaintext Attack:** Attacker can query $F_k()$
- **Chosen-ciphertext Attack:** Attacker can query $F_k()$ and $F_k^{-1}()$

## Procedure

Plaintext is encrypted one block at a time, and ciphertext is decrypted one block at a time.

## Confusion and Diffusion

- **Confusion**
  - Small change in input to the step yield small, random change in output of the step.
  - To make the relation between the ciphertext and the key a very complex and involved one.
  - Each bit of the ciphertext block has highly nonlinear relations with the key bits.
- **Diffusion**
  - Small change in input to the step should be propagated to affect entire output of the step.
  - Each plaintext block bit or key bit affects many bits of the ciphertext block.
  - **Avalanche Effect:** Small modification cause big impact.

## Substitution-Permutation Networks (SPNs)

A substitution-permutation network (SPN) can be viewed as a direct implementation of the confusion-diffusion paradigm.

The round function has a particular form: $f_{k_i}(x) = S_i{(k_i \oplus x)}$, where $S_i$ is a fixed public permutation, and it is called **S-box** (substitution box).

XORing the key is called **key mixing**.

### A 1-Round SPN

1. Key mixing - Add round key
   - Mixing operation between the round input and the round key
   - Add randomization
2. Substitution - Confusion layer
   - Makes the relationship between round input and output complex.
   - A nonlinear layer
   - Add confusion
   - Achieved by small substitution functions
3. Permutation (mixing) - Diffusion layer
   - A linear layer for spreading - avalanche effect
   - Add diffusion
   - Achieved diffusion by using permutations, linear transformation of the inputs

### An $r$-Round SPN

A $r$-round SPN has $r$ rounds repetitions of the key mixing, substitution, and mixing permutation for $r$ iterations, and there is a final key mixing step after the last round.

A single secret key is used to generate each round's key, which is called key expansion.

### Design of S-boxes and Mixing Permutation

S-boxes should ensure that any 1-bit change in input should cause at least 2-bit change in output. And S-boxes are nonlinear transformations.

Mixing permutation should ensure that each bit output from a given S-box should feed into a different S-box in the next round.

## Feistel Networks

A feistel network builds invertible permutation from non-invertible components, and it opeartes in a series of rounds.

A keyed round function is applied in each round.

The input is divided into two parts, $L$ and $R$, where $L$ is the left half part of the input, while $R$ is the right half part of the input.

In one round:

- Keyed round function $f: \{0,1\}^n \times \{0,1\}^{\ell / 2} \rightarrow \{0,1\}^{\ell / 2}$
- $F_{k_1}(L_0,R_0) \rightarrow (L_1,R_1) = (R_0,L_0 \oplus f_{k_1}(R_0))$

And the round function need not be invertible.

---
# prettier-ignore
date: 2026-05-01
title: Classical Cryptography
description: Introduction of classical cryptography.
weight: 3
---

## Private-key Cryptography

### Symbols

| Notation | Definition               |
| -------- | ------------------------ |
| $k$      | Secret key               |
| $K$      | Key space                |
| $c$      | Ciphertext               |
| $m$      | Message / plaintext      |
| $M$      | Message space            |
| $Gen$    | Key-generation algorithm |
| $Enc$    | Encryption algorithm     |
| $Dec$    | Decryption algorithm     |

### Encryption and Decryption Process

- Key-generation:

  Use the algorithm $Gen$ to generate a secret key $k \in K$

- Encryption:

  Input the secret key $k$, and a message $m \in M$

  Output the ciphertext $c$

  $$
  c \gets Enc_k(m)
  $$

- Decryption

  Input the secret key $k$, and the ciphertext $c$

  Output the plaintext $m$, or **an error**

  $$
  m \coloneqq Dec_k(c)
  $$

## Kerckhoffs’s Principle

- The encryption scheme is not secret
  - The attacker knows the encryption scheme
  - Only the key is secret
  - The key must be chosen randomly, and be kept secretly

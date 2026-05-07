---
# prettier-ignore
date: 2026-05-07
title: Stream Cipher
weight: 9
---

## Binary Additive Stream Cipher

### Encryption Process

- The keystream generator takes input a short key and may be some additional public information
- The keystream generator outputs a longer pseudo-random sequence, called the **keystream**
- Each plaintext bit is XORed with the corresponding keystream bit to produce the ciphertext bits

### Decryption Process

- The same key is input to the keystream generator
- Generate the same pseudo-random keystream of required length at the receiver
- XOR each of the ciphertext bit with the corresponding keystream bit to recover the plaintext bits

### Initialization Vector (IV)

Most modern stream ciphers use two inputs: a secret key, and a known initialization vector (IV).

The IV is also called a _nonce_.

A new different keystream can be formed using the same key by changing the IV.

The IV can be the frame number, the packet number, etc. And the IV is made public, only the key is secret.

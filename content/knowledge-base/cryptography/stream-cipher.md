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

## Design a Good Keystream Generator

A good keystream generator should have the following properties:

- Correlation immunity
- High algebraic degree (non-linearity)
- Large period

### Correlation Immunity

A good keystream generator should not have significant correlation with the input bits.

For example, $Z = (a \land b) \oplus ((\lnot a) \land c)$, the truth table is:

| $a$ | $b$ | $c$ | $Z$ |
| --- | --- | --- | --- |
| $0$ | $0$ | $0$ | $0$ |
| $0$ | $0$ | $1$ | $1$ |
| $0$ | $1$ | $0$ | $0$ |
| $0$ | $1$ | $1$ | $1$ |
| $1$ | $0$ | $0$ | $0$ |
| $1$ | $0$ | $1$ | $0$ |
| $1$ | $1$ | $0$ | $1$ |
| $1$ | $1$ | $1$ | $1$ |

Where the output $Z$ has $75\%$ time to follow $b$, and $75\%$ time to follow $c$, which enables attackers to guess possible input bits according to $Z$.

### High Algebraic Degree

A good keystream generator should have a high degree output polynomial to avoid higher order differential attack, cube attack, chosen IV statistical attack, etc.

For example, a function's degree can be decreased by differentiation, and the summation of the derivative can sometimes leak information about secret keys. So a high degree output function is required to prevent this kind of attack.

### Large Period

If the output keystream has a short period, the result may be:

- The same keystream will be generated in a short period of time
- The same keystream sequence will be used to encrypt multiple segment of the plaintext

These results make ciphertext only attack and known plaintext attack possible.

So, a good keystream should have a long period.

## Modern Stream Ciphers

Modern stream cipher combines LFSRs and NFSRs to control the period and complexity.

### Procedure

- **Initialization Phase**
  - Load the key and the IV into the state
  - Update the cipher for a number of rounds without producing any output keystream, to get the key and IV mixed well.
- **Encryption Phase**
  - Begins at the initial state
  - Generate keystream based on the output function
  - Combine the keystream with the plaintext to produce the ciphertext
- **Decryption Phase**
  - Begins at the initial state
  - Generate keystream based on the output function
  - Combine the keystream with the ciphertext to produce the plaintext

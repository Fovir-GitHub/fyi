---
# prettier-ignore
date: 2026-05-01
title: Introduction
description: Introduction of cryptogarphy.
weight: 2
---

## Security Goals

The traditional goal of cryptography is to achieve **CIA:**

- **C**onfidentiality: Prevent the unauthorized disclosure of information.
- **I**ntegrity: Detect the unauthorized modification or destruction of information.
- **A**vailability: Ensure resources are accessible when required by an authorized entity.

Additional goals:

- **Authentication:** Process of verifying something to be true.
- **Non-repudiation:** Create evidence that an action has occurred, and the user cannot falsely deny the action.

## Security and Obscurity

Obscurity is like _hidden_, while security means sharing or delivering safely.

## Cryptographic Terminology

- Plaintext ($P$): The original message or data
- Encryption ($E$): Plaintext → Ciphertext
- Cryptographic Key ($K$): Secret key
- Cipher: Algorithm that transforms the message
- Ciphertext ($C$): Encrypted messages
- Decryption ($D$): Ciphertext → Plaintext

## Encoding and Encryption

Encoding allows anyone who knows the corresponding decoding algorithm to decode the message or data.

```mermaid
graph LR
  od["Original Data"] <--> |Algorithm| ed["Encoded Data"]
```

On the other hand, to decrypt an encrypted message, both decryption algorithm and secret key should be known.

```mermaid
graph LR
  pt["Plaintext"] <-->|"Algorithm & Secret key"| ct["Ciphertext"]
```

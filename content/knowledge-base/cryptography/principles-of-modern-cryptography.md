---
# prettier-ignore
date: 2026-05-03
title: Principles of Modern Cryptography
description: Note of principles of modern cryptography.
weight: 5
---

## Core Principles

The goal is to provide a rigorous proof that a given construction is secure.

The formal definitions should be precise, and be a mathematical model.

Assumptions should be clearly stated and unambiguous.

## Secure Encryption Scheme Guaranty

Regardless of any information an attacker already has, a ciphertext should not leak additional information about the underlying plaintext.

## Thread Models for Encryption

- **Ciphertext-only Attack:** Adversary just observes one of more ciphertexts.
- **Known-plaintext Attack:** Adversary is able to learn one or more plaintext/ciphertext pairs generated using some keys.
- **Chosen-plaintext Attack:** Adversary can obtain plaintext/ciphertext pairs for plaintext of its choice.
- **Chosen-ciphertext Attack:** Adversary is additionally able to obtain some information about the decryption of ciphertexts of its choice.

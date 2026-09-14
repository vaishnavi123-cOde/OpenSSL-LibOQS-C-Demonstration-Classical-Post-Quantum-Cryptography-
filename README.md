# OpenSSL & LibOQS C Demonstration (Classical & Post-Quantum Cryptography)

This repository contains a C implementation demonstrating symmetric encryption using OpenSSL and Post-Quantum Cryptography (PQC) Key Encapsulation Mechanism (KEM) using `liboqs`.

## Overview

The demonstration covers two foundational cryptographic operations implemented in standard C (C99):

1. **Classical Symmetric Encryption (OpenSSL EVP API)**:
   - **Algorithm**: AES-256-GCM (Galois/Counter Mode)
   - **Key/IV Generation**: Cryptographically secure pseudo-random generation via `RAND_bytes`.
   - **Operations**: Plaintext encryption, initialization vector (IV) handling, and GCM authentication tag extraction.

2. **Post-Quantum Cryptography (LibOQS KEM API)**:
   - **Algorithm**: Kyber-768 (NIST ML-KEM-768 standard candidate)
   - **Operations**:
     - Keypair generation (Public Key / Secret Key).
     - Shared secret encapsulation (Client side).
     - Shared secret decapsulation (Server side).
     - Byte-level verification of derived shared secrets.
     - Secure memory sanitization using `OQS_MEM_cleanse`.

---

## Environment & Dependencies

- **OS / Runtime**: Ubuntu / Linux (WSL2 / Google Colab tested)
- **Compiler**: GCC / Clang
- **Libraries**:
  - `libcrypto` (OpenSSL 3.x development headers)
  - `liboqs` (Open Quantum Safe C library)

---

## Build & Execution Instructions

### 1. Install Prerequisites & Build LibOQS
```bash
sudo apt-get update
sudo apt-get install -y libssl-dev cmake build-essential git

git clone -b main [https://github.com/open-quantum-safe/liboqs.git](https://github.com/open-quantum-safe/liboqs.git)
cd liboqs
mkdir build && cd build
cmake -DCMAKE_INSTALL_PREFIX=/usr -DBUILD_SHARED_LIBS=ON ..
make -j$(nproc)
sudo make install
sudo ldconfig

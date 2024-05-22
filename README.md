Based on the code and content from the notebook, here is a README for your project:

---

# AES Encryption and Decryption

This project implements the Advanced Encryption Standard (AES) algorithm in Python. It includes both the encryption and decryption processes, along with the necessary supporting functions and data structures.

## Objective

To provide a detailed and educational implementation of the AES algorithm, focusing on understanding the underlying mathematics and operations involved in both encryption and decryption.

## Features

- **AES Encryption**: Implements the AES encryption process including key expansion, substitution, shift rows, mix columns, and add round key operations.
- **AES Decryption**: Implements the AES decryption process with inverse operations for substitution, shift rows, mix columns, and add round key.
- **Polynomial Reduction**: Handles polynomial reduction in Galois Field (GF) \(2^8\) using AES's irreducible polynomial.
- **Affine Mapping**: Includes affine mapping for generating the S-box and its inverse.
- **Precomputed Tables**: Uses precomputed tables for S-box and inverse S-box for efficiency.

## Code Overview

### Polynomial Reduction and Multiplication

The polynomial reduction in GF \(2^8\) is based on the irreducible polynomial \(P(X) = X^8 + X^4 + X^3 + X + 1\).

```python
def PofX(x):
    return (((x << 1) ^ (0x1B if x & 0x80 else 0x00)) & 0xFF)

def Multi(x, y):
    result = 0
    for i in range(8):
        if y & (1 << i):
            result ^= x
        x = PofX(x)
    return result
```

### S-box Generation

The S-box is generated using the multiplicative inverse in GF \(2^8\) followed by an affine transformation.

```python
def InverseOperation(x):
    return inverse_table[x]

def AffineMapping(x):
    y = 0
    for i in range(8):
        y |= ((((x >> i) ^ (x >> ((i + 4) % 8)) ^ (x >> ((i + 5) % 8)) ^ (x >> ((i + 6) % 8)) ^ (x >> ((i + 7) % 8)) ^ (0x63 >> i)) & 1) << i)
    return y
```

### Encryption Process

The encryption process includes key expansion, SubBytes, ShiftRows, MixColumns, and AddRoundKey operations.

```python
def AES_Encryption(plaintext, key):
    # Key expansion
    # Initial AddRoundKey
    # Rounds of SubBytes, ShiftRows, MixColumns, AddRoundKey
    # Final round without MixColumns
    pass
```

### Decryption Process

The decryption process includes inverse operations for SubBytes, ShiftRows, MixColumns, and AddRoundKey.

```python
def AES_Decryption(ciphertext, key):
    # Key expansion
    # Initial AddRoundKey
    # Rounds of InvShiftRows, InvSubBytes, InvAddRoundKey, InvMixColumns
    # Final round without InvMixColumns
    pass
```

## Running the Code

To run the code, ensure you have Python installed. You can execute the provided functions in a Python environment. The notebook format allows for step-by-step execution and visualization of intermediate steps and results.

## Output

The code includes print statements to display intermediate results like the S-box, inverse S-box, and the final ciphertext to verify the correctness of the implementation.

```python
print("AES S-box:", S_box)
print("Inverse S-Box:", inv_S_box)
print("Ciphertext:", ciphertext)
```

## Contributions

Contributions are welcome! Please fork the repository and submit a pull request with your changes.

## Acknowledgments

This project was developed as part of a cryptography course and is intended for educational purposes.

---

This README provides an overview of the project, explaining its purpose, features, code structure, and how to run the code.

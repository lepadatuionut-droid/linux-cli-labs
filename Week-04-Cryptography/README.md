
# Week 4 – Cryptography (Kali / Apporto)

This lab focused on **cryptography fundamentals using GNU Privacy Guard (GPG)** in Kali Linux — essential for protecting sensitive information in cybersecurity systems.

Tasks included:

* verifying cryptographic tools
* creating plaintext files
* encrypting and decrypting files using **AES-256 symmetric encryption**
* generating **RSA asymmetric key pairs**
* identifying where cryptographic keys are stored in Linux

Cryptography ensures secure communication by providing **confidentiality, integrity, authentication, and non-repudiation**.

*(Reference: CyberSec Tutorial Week 4 document)*

---

# 1. Checking Encryption Tools (GPG)

Using:

```
gpg --version
```

This command verifies that **GNU Privacy Guard (GPG)** is installed in Kali Linux.

The output shows:

* installed version of GPG
* supported encryption algorithms (AES, RSA)
* supported hashing algorithms (SHA)

GPG is an open-source implementation of **OpenPGP encryption**, widely used for secure communication and file protection.

---

# 2. Creating a Plaintext File

Create a file to demonstrate encryption.

```
touch encrypt.txt
echo "I need to be encrypted" > encrypt.txt
cat encrypt.txt
```

The file now contains readable **plaintext data**.

Plaintext represents information before encryption is applied.

---

# 3. Symmetric Encryption (AES-256)

Encrypt the file using **AES-256 symmetric encryption**.

```
gpg --symmetric --cipher-algo AES256 encrypt.txt
```

Passphrase used:

```
Kali123@
```

What happens internally:

* the original file remains unchanged
* a new encrypted file is created

```
encrypt.txt.gpg
```

AES-256 is a strong symmetric encryption algorithm commonly used in modern security systems.

Symmetric encryption means:

* the **same key (passphrase)** is used for encryption and decryption.

---

# 4. Viewing Ciphertext

Display encrypted file contents:

```
cat encrypt.txt.gpg
```

The output appears as **random unreadable characters**.

This data is called **ciphertext**, which cannot be understood without the correct decryption key.

This confirms the encryption process was successful.

---

# 5. Organising Encrypted Files

Create a directory to store encrypted files.

```
mkdir Encrypt_Directory
mv encrypt.txt.gpg Encrypt_Directory
cd Encrypt_Directory
ls
```

The encrypted file is now stored inside:

```
Encrypt_Directory
```

This demonstrates proper **secure file organisation** practices.

---

# 6. Decrypting the File

Decrypt the encrypted file using the original passphrase.

```
gpg -o decrypt.txt -d encrypt.txt.gpg
```

Explanation:

* `-d` → decrypt file
* `-o decrypt.txt` → specify output filename

Verify decrypted content:

```
cat decrypt.txt
```

Output:

```
I need to be encrypted
```

The original plaintext is restored successfully.

---

# 7. Generating Asymmetric Key Pairs

Generate an **RSA key pair**.

```
gpg --full-generate-key
```

Configuration used:

* Algorithm: RSA
* Key size: 3072 bits
* Expiry: No expiration

The process creates two keys:

| Key         | Purpose      |
| ----------- | ------------ |
| Public Key  | Encrypt data |
| Private Key | Decrypt data |

Asymmetric encryption solves the **key-exchange problem** present in symmetric cryptography.

---

# 8. Listing Public and Private Keys

Public keys:

```
gpg --list-keys
```

Private keys:

```
gpg --list-secret-keys
```

These commands display key information including:

* key ID
* algorithm type
* user identity
* creation date

---

# 9. Locating Cryptographic Key Storage

GPG stores keys inside the user home directory.

Display hidden files:

```
ls -a $HOME
```

Hidden directory:

```
.gnupg
```

Inside `.gnupg`:

| File / Directory  | Purpose                    |
| ----------------- | -------------------------- |
| private-keys-v1.d | stores private keys        |
| pubring.kbx       | stores public keys         |
| trustdb.gpg       | stores trust relationships |

This directory contains all GPG cryptographic material.

---

# 10. Security Relevance in Cybersecurity

Cryptography protects data from unauthorized access.

Key security applications include:

* secure communication
* email encryption (PGP)
* digital signatures
* file integrity verification

Symmetric encryption (AES) is used for **fast data encryption**, while asymmetric encryption (RSA) enables **secure key exchange**.

Incorrect key management can compromise security systems, making cryptography a critical skill for cybersecurity professionals.

---

# 11. Evidence

Full screenshots documenting the lab steps are stored in:

```
docs/Week_4_LAB.docx
```

Individual screenshots are located under:

```
screenshots/
```

Example evidence includes:

* verifying GPG installation
* plaintext file creation
* AES-256 encryption
* ciphertext verification
* decryption process
* RSA key pair generation
* key listing commands

---

 

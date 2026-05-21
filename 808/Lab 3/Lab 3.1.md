# ✅ WHAT YOU NEED TO DO IN THE CONFIDENTIALITY LAB

Lab focuses on the CIA Triad, but in this manual you will perform tasks only for the Confidentiality pillar.

You will perform 3 main tasks:

# **🔵 PART 1 — Data Encoding & Decoding (Base64 and Hex)**

### ✔ 1. Base64 Encoding

Open terminal and run:

```
echo -n 'Hello, Base64!' | base64
```

### ✔ 2. Base64 Decoding

```
echo -n 'SGVsbG8sIEJhc2U2NCENCg==' | base64 --decode
```

### ✔ 3. Hex Encoding

```
echo -n 'Hello, Hex!' | xxd -p
```

### ✔ 4. Hex Decoding

```
echo -n '48656c6c6f2c2048657821' | xxd -r -p
```

📌 **Goal:** Understand that encoding is reversible and NOT encryption.

---

# **🟢 PART 2 — Symmetric Encryption & Decryption (AES)**

You will use **AES-256-CBC** with `openssl`.

### ✔ 1. Create a plaintext file

```
echo "this is plaintext" > plain.txt
cat plain.txt
```

### ✔ 2. Encrypt using AES

```
openssl enc -pbkdf2 -aes-256-cbc -in plain.txt -out output.txt
```

Then view encrypted text:

```
cat output.txt
```

### ✔ 3. Decrypt using AES

```
openssl enc -d -pbkdf2 -aes-256-cbc -in output.txt -out data.txt
cat data.txt
```

📌 **Goal:** Learn symmetric encryption—same key is used for encrypting & decrypting.

---

# **🔴 PART 3 — Asymmetric Encryption & Decryption (RSA)**

Here you will create **RSA keys**, then encrypt with the **public key** and decrypt with the **private key**.

### ✔ 1. Generate Private Key

```
openssl genrsa -out private.key 2048
```

### ✔ 2. Generate Public Key

```
openssl rsa -pubout -in private.key -out public.key
```

### ✔ 3. Create a plaintext file

```
echo "this is plaintext of asymmetric" > plaintext.txt
cat plaintext.txt
```

### ✔ 4. Encrypt using RSA public key

```
openssl pkeyutl -encrypt -in plaintext.txt -out pmics_encrypted.txt -pubin -inkey public.key
cat pmics_encrypted.txt
```

### ✔ 5. Decrypt using RSA private key

```
openssl pkeyutl -decrypt -in pmics_encrypted.txt -out pmics_decrypted.txt -inkey private.key
cat pmics_decrypted.txt
```

📌 **Goal:** Learn asymmetric encryption — encrypt with **public key**, decrypt with **private key**.

---








# Secure Text Editor

A desktop text editor in Java (Swing) that can save files encrypted with **AES** or the **Vigenère cipher**, and open them again with the right key.

**Course:** ITCS461 Computer and Communication Security, MUICT

## Features

- New, open, save, print
- Save as encrypted:
  - **Vigenère cipher** (`.encv`): works on printable ASCII characters (32–126); other characters are kept as-is
  - **AES** (`.enca`): AES/ECB/PKCS5Padding with a 128-bit key derived from your password (SHA-1), Base64-encoded
- Opening an `.encv` or `.enca` file asks for the key and shows the decrypted text; a wrong AES key shows an error
- Edit: cut, copy, paste, delete, select all, insert time and date
- Format: word wrap
- View: zoom in, zoom out, reset zoom
- Status bar and a prompt before discarding unsaved changes

> This is a learning project. ECB mode and a SHA-1–derived key are not suitable for protecting real data; use a vetted tool for that.

## Requirements

Java 8 or newer (JDK).

## Run

From the project folder:

```bash
mkdir -p bin
javac -d bin src/*.java
cp src/secure.png bin/
java -cp bin SecureTextEditor
```

Or import the folder into Eclipse as an existing project (the `.project` and `.classpath` files are included) and run `SecureTextEditor`.

To try the ciphers without the UI, `AES` and `VigenereCipher` each have a small `main` method that encrypts and decrypts a sample string.

## Project structure

```
src/
├── SecureTextEditor.java   # Swing UI: menus, file handling, encrypt/decrypt flow
├── AES.java                # AES encryption and decryption
├── VigenereCipher.java     # Vigenère cipher over printable ASCII
└── secure.png              # Window icon
```

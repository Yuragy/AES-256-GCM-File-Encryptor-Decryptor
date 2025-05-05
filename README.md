# AES-256 GCM File Encryptor / Decryptor
A pair of standalone console utilities for encrypting and decrypting files and folders using AES-256 in GCM mode.
## Overview
This repository contains two independent applications:
1. **Encryptor** (encryptor.exe)  
   Recursively traverses a folder and encrypts each file into a separate .enc file.
2. **Decryptor** (decryptor.exe)  
   Recursively traverses a folder of .enc files and restores the originals.

Both utilities use AES-256-GCM from the cryptography library, with a 12-byte IV and 16-byte authentication tag.

## Features
- **Secure Encryption**  
  – AES-256 in GCM mode with built-in authentication.  
- **Batch Processing**  
  – Recursively processes all files in a given directory.  
- **Simple CLI**  
  – Prompts for folder path and key.  
- **Standalone EXE Builds**  
  – Packaged into single executables using PyInstaller.  

## Requirements
- Python 3.8 or higher  
- cryptography library  
- (For building) PyInstaller

## Usage
### Encrypting a Folder

1. Run the encryptor:
   encryptor.exe
   or
   python encrypt.py
2. When prompted, enter the folder path:
   Enter folder path to encrypt: C:\folder
3. Enter a 16-character key:
   Enter key (exactly 16 characters)
4. Result:
   * A new folder folder_encrypted is created.
   * Each file is encrypted and saved with a .enc extension.

### Decrypting a Folder
1. Run the decryptor:
   decryptor.exe
   or
   python decrypt.py
2. When prompted, enter the folder path:
   Enter folder path to decrypt: C:\path\to\folder_encrypted
3. Enter the same 16-character key:
   Enter key (exactly 16 characters): mysecretpassword
4. Result:
   * A new folder folder_decrypted is created.
   * Each .enc file is decrypted back to its original form.

## Parameters & Limitations
* **Key Length:** Exactly 16 characters (128 bits).
* **IV:** 12 random bytes, prepended to each .enc file.
* **Auth Tag:** 16 bytes, appended to each .enc file.
* **Chunk Size:** 64 KiB for streaming large files.
* **Note:** Although AES-256 expects a 32-byte key, this implementation uses a 16-byte key for simplicity.

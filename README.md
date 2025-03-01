# GPG stuff

A script to generate a message and sign it with GPG.

## Prerequisites

- GPG installed (`brew install gpg`)
- Public key
- Make the scripts executable (`chmod +x gpg-encrypt.sh gpg-decrypt.sh`)

## Create a public key(optional)

```bash
gpg --generate-key
```

## Encrypt

The gpg-encrypt.sh script encrypts a file using the recipient's public key.

```bash
sh gpg-encrypt.sh -e email@example.com -f message.txt -pk public-key.asc

## Example
# Export your public key (if not already done)
gpg --armor --export recipient@example.com > public-key.asc

# Encrypt a message using the public key
sh gpg-encrypt.sh -e recipient@example.com -f message.txt -pk public-key.asc

```

### Test

```bash
gpg --full-generate-key
gpg --armor --export recipient@example.com > public-key.asc

sh gpg-encrypt.sh -e recipient@example.com -f message.txt -pk public-key.asc
gpg --decrypt message.txt.asc

```

## Decrypt

```bash
sh gpg-decrypt.sh -f message.txt.asc
```

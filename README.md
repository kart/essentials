# Essential tutorial bits for developers
This document is a collection of tutorial bits that I gather over time from
topics ranging from simple bash commands and git gems to creating self-signed
certifcates. It helps to have a common place to store these gems which can be
easily searched.

## Git
- List branches that contain a given commit
```bash
# search within a local branch
$ git branch --contains <commit>
# search across local and remote branches
$ git branch -r --contains <commit>
```

- List all commits in the current branch that are not in the remote branch
```bash
git cherry -v
```

- For a given file, find what commits were added to master relative to the local
  branch
```bash
git log --oneline HEAD..master -- <file>
```

- Change the author
```bash
git commit --amend --author="<Author Name> <email@address.com>"
```

- Show git root directory
```bash
git rev-parse --show-toplevel
```

## Certificate generation
- Generate a keystore using the Java keytool
```bash
keytool -genkey -alias server -keyalg RSA -keysize 2048 -keystore cloud.jks
```
- Generate a certificate request
```bash
keytool -certreq -alias server -file cloud.csr.txt -keystore cloud.jks
```
- Import one or all entries from another keystore
```bash
keytool -importkeystore -srckeystore cloud.jks -destkeystore cloud.pkcs -srcstoretype JKS  -deststoretype PKCS12
```
- Generate a PEM from a pkcs12 formatted file
```bash
openssl pkcs12 -in cloud.pkcs -out cloud.pem
```
- Reveal the private key from the PEM file
```bash
openssl rsa -in cloud.pem -out cloud.key
```
- Generate a certificate from the certificate request and private key
```bash
openssl x509 -req -days 365 -in cloud.csr.txt -signkey cloud.key -out cloud.crt
```
- Convert CRT to PEM format
```bash
openssl x509 -in cloud.crt -out cloud.pem -outform PEM
```


## USEFULL OPENSLL COMMANDS


- SSL - Secure Socket Layer
- CSR - Certificate Signing Request
- TLS - Transport Layer Security
- PEM - Privacy Enhanced Mail
- DER - Distinguished Encoding Rules
- SHA - Secure Hash Algorithm
- PKCS - Public-Key Cryptography Standards

---
#### Create new Private Key and Certificate Signing Request
```bash
openssl req -out domain.csr -newkey rsa:2048 -nodes -keyout domain.key
```
#### Create a Self-Signed Certificate
```bash
openssl req -x509 -sha256 -nodes -newkey rsa:2048 -keyout selfsigned.key -out cert.pem
openssl req -x509 -sha256 -nodes -days 360 -newkey rsa:2048 -keyout selfsigned.key -out cert.pem
```

#### Verify CSR file
```bash
openssl req -noout -text -in domain.csr
```

#### Create RSA Private Key
```bash
openssl genrsa -out private.key 2048
```

#### Remove Passphrase from Key
```bash
openssl rsa -in certkey.key -out nopassphrase.key
```

#### Verify Private Key
```bash
openssl rsa -in certkey.key -check
```

#### Verify Certificate File
```bash
openssl x509 -in certfile.pem -text -noout
```

#### Verify the Certificate Signer Authority
```bash
openssl x509 -in certfile.pem -noout -issuer -issuer_hash
```

#### Check Hash Value of A Certificate
```bash
openssl x509 -noout -hash -in domain.pem
```

#### Convert DER to PEM format
```bash
openssl x509 -inform der -in sslcert.der -out sslcert.pem
```

#### Convert PEM to DER format
```bash
openssl x509 -outform der -in sslcert.pem -out sslcert.der
```

#### Convert Certificate and Private Key to PKCS#12 format
```bash
openssl pkcs12 -export -out sslcert.pfx -inkey key.pem -in sslcert.pem
```

#### Convert Certificate and Private Key to PKCS#12 format with chain
```bash
openssl pkcs12 -export -out sslcert.pfx -inkey key.pem -in sslcert.pem -chain cacert.pem
```

#### Create CSR using an existing private key
```bash
openssl req -out certificate.csr -key existing.key -new
```

#### Check contents of PKCS12 format cert
```bash
openssl pkcs12 -info -nodes -in cert.p12
```

#### Convert PKCS12 format to PEM certificate
```bash
openssl pkcs12 -in cert.p12 -out cert.pem
```

#### Test SSL certificate of particular URL
```bash
openssl s_client -connect yoururl.com:443 -showcerts
```

#### Find out OpenSSL version
```bash
openssl version
```

#### Check PEM File Certificate Expiration Date
```bash
openssl x509 -noout -in certificate.pem -dates
```

#### Check Certificate Expiration Date of SSL URL
```bash
openssl s_client -connect targeturl.com:443 2>/dev/null | openssl x509 -noout -enddate
```

#### Check if SSL V2 or V3 is accepted on URL
```bash
openssl s_client -connect targeturl.com:443 -ssl2
openssl s_client -connect targeturl.com:443 -ssl3
openssl s_client -connect targeturl.com:443 -tls1
openssl s_client -connect targeturl.com:443 -tls1_1
openssl s_client -connect targeturl.com:443 -tls1_2
```

#### Verify if the particular cipher is accepted on URL
```bash
openssl s_client -cipher 'ECDHE-ECDSA-AES256-SHA' -connect targeturl:443
```

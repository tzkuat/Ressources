# OpenSSL Cheat Sheet

More information :
* [Net-Security OpenSSL Cheat-Sheet](https://net-security.fr/security/openssl-formats-cheat-sheet/)
* [Net-Security OpenSSL ECC](https://net-security.fr/security/openssl-ecc/)
* [OpenSSL](https://www.openssl.org/)

## Summary
* [Classic Commands](#Classic-Commands)
* [ECC Commands](#ECC-Commands)

## Classic Commands

#### Create RSA private key
```
openssl genrsa -out www.example.com.key 2048
```

#### Generate CSR whith new private key
```
openssl req -sha256 -nodes -newkey rsa:2048 -keyout www.example.com.key -out www.exempla.com.csr
```

#### Generate CSR whith existent private key
```
openssl req -new -sha256 -key www.example.com.key -out www.example.com.csr
```

#### Generate CSR with existant certificate and private key
```
openssl x509 -x509toreq -in www.example.com.crt -out www.example.com.csr -signkey www.example.com.key
```

#### Generate sign-auto certificate for 1 year 
```
openssl req -x509 -newkey rsa:2048 -nodes -keyout www.example.com.key -out www.example.com.crt -days 365
```

#### Print certificate information
```
openssl x509 -in certificate.crt -text -noout
```

#### Print CSR information
```
openssl req -text -noout -verify -in CSR.csr
```

#### Print private key information
```
openssl rsa -noout -text -check -in www.example.com.key
```

#### Print P12 certificate information
```
openssl pkcs12 -info -in KEYSTORE.p12
```

#### Print and test certificate in a server
```
openssl s_client -connect www.example.com:443
```

#### Print and verify modulus of private key, CSR & certificate with hash of modulus
```
openssl x509 -noout -modulus -in www.example.com.crt | openssl sha256
openssl req -noout -modulus -in www.example.com.csr | openssl sha256
openssl rsa -noout -modulus -in www.example.com.key | openssl sha256
```

#### PEM format to P12 format
```
openssl pkcs12 -export -inkey private.key -in certificate.crt -certfile chain.pem -out keystore.pfx
```

#### Certifiate and private key in same file (PEM)
```
cat cert.crt key.key > pem.pem
```

#### Extract certificate and private key from a P12/PFX
```
openssl pkcs12 -in keystore.pfx -out certificate.crt –nokeys
openssl pkcs12 –in keystore.pfx -out key.key -nocerts –nodes
```

#### PKCS8 private key to PKCS1
```
openssl rsa -in key.key -out key2.key
```

#### PKCS1 private key to PKCS8
```
openssl pkcs8 -topk8 -inform PEM -outform PEM -nocrypt -in pkcs1.key -out pkcs8.key 
```

#### DER (binary) private key to PEM
```
openssl rsa -inform der -in der_key.der -out pem_key.key
```

#### PEM private key to DER
```
openssl rsa -inform PEM -outform der -in pem_key.key -out der_key.der 
```

#### DER certificate to PEM
```
openssl x509 -inform der -in certificateder.cer -out certificatepem.crt
```

#### PEM certificate to DER
```
openssl x509 -outform der -in certificatepem.crt -out certificateder.cer
```

## ECC Commands

#### List curves 
```
openssl ecparam -list_curves 
```

#### Generate private key
```
openssl ecparam -genkey -name prime256v1 -out key.key
```

#### Add passphrase to private key
```
openssl ec -in example.key -des3 -out example.key
```

#### Generate CSR 
```
openssl req -new -sha256 -key example.key -nodes -out example.csr
```

#### Generate certificate
```
openssl req -x509 -sha256 -days 365 -key key.pem -in csr.csr -out certificate.pem
```

#### Print public key of private key
```
openssl ec -in example.key -pubout
```

#### Print public key of CSR 
```
openssl req -in example.csr -pubkey -noout 
```

#### Print public key of certificate 
```
openssl x509 -in example.crt -pubkey -noout 
```

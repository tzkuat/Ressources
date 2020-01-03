# GPG Cheat Sheet

## Command 

#### Generate GPG key pair with full option
```
gpg --full-gen-key
```

#### Generate GPG key pair
```
gpg --gen-key
```

#### List key pair 
```
gpg --list-keys
```

#### List public keys
```
gpg -k
```

#### List private keys 
```
gpg -K 
```

#### Find fingerprint  
```
gpg --fingerprint ID_KEY
```

#### Export public key in file 
```
gpg --export --armor ID_KEY > out.key
```

#### Import public key from a file 
```
gpg --import file.key
```

#### List key pair 
```
gpg --list-keys
```

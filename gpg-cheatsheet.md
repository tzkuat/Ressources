# GPG Cheat Sheet

More information :
* [Net-Security GPG Cheat-Sheet](https://net-security.fr/security/gnupg-introduction-cheat-sheet/)
* [The GNU Privacy Guard](https://gnupg.org/)

## Summary
* [GPG Linux config file](#Config file)
* [GPG Linux commands list](#Commands)

## Config file

## Commands

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

#### Export public key in a file 
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

#### Export private key in a file
```
gpg --export-secret-key -a > out.key
```

#### Import private key from a file
```
gpg --import --allow-secret-key-import fichier_cle.key
```

#### Sign a file
```
gpg -s -u ID_KEY file
gpg -s file (with default key)
```

#### Encrypt a file
```
gpg -r ID_KEY -e -a file
```

#### Encrypt and sign a file
```
gpg -s -a -e -u ID_KEY file
```

#### Decrypt a file
```
gpg -r ID_KEY -d file
```

#### Verify external signature
```
gpg --verify file file_sign
```

#### Verify Signature
```
gpg --verify file
```

#### Delete key (public & private)
```
gpg --delete-secret-keys ID_KEY
gpg --delete-key ID_KEY
```

#### Find technical information 
```
gpg --edit-key ID_KEY
```
* Verify signature of a key
```
> check
```
* List preferences
```
> pref
> showpref
```

#### Change passphrase of private key 
```
gpg --edit-key ID_KEY
> passwd
> save 
```

#### Sign a public key 
```
gpg --sign-key ID_KEY_TO_SIGN
```

#### Verify key signature
```
gpg2 --edit-key ID_KEY_
> check 
```

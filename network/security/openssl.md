# OpenSSL

## Generieren
### Erzeugen von einem private Key
```linux
# RSA
openssl genrsa -out private_key.pem 4096
```

### Erzeugen von Certificate Signing Requests (CSRs)
```linux
# Mit einem neuen Schlüssel
$ openssl req \
          -out <csr>.csr \
          -new -newkey rsa:2048 \
          -nodes -keyout <private-key>.key

# Auf der Basis von einem vorhandenen Schlüssel
$ 
```

### Generieren von Zertifikaten
```linux
# Mit CNF-File
openssl req -new -x509 \
        -key private_key.pem \
        -out public_key.pem \
        -days 365 \
        -config configfile.cnf
```

## Konvertieren
### crt-Datei -> pkcs12
```linux
$ openssl pkcs12 -export -in </path/to/cert/file> -inkey <path/to/private/key/file> -out </path/p12/key/file> 
```

## Prüfen
```linux
# Public-Key
$ openssl x509 -noout -modulus -in <public-key-file>.crt | openssl md5

# Private Key
$ openssl rsa -noout -modulus -in <private-key-file>.key | openssl md5
```

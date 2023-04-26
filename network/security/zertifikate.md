# Zertifakte und Keystores

## Generieren
### Erzeugen von Certificate Signing Requests (CSRs)
```linux
# Mit einem neuen Schlüssel
$ openssl req -out <csr>.csr -new -newkey rsa:2048 -nodes -keyout <private-key>.key

# Auf der Basis von einem vorhandenen Schlüssel
$ 

# Validieren von Zertifikaten
```

## Konvertieren
### crt-Datei -> pkcs12
```linux
$ openssl pkcs12 -export -in </path/to/cert/file> -inkey <path/to/private/key/file> -out </path/p12/key/file> 
```

### pkcs12 -> jks
```linux
$ keytool -importkeystore \
          -srckeystore <path/to/p12/keystore/file> \
          -srcstoretype pkcs12 \
          -destkeystore <path/to/jks/keystore> \
          -deststoretype JKS
```

## Importieren
### crt-Datei -> jks
```linux
$ keytool -importcert -file <path/to/cert/file> -keystore <path/to/jks/keystore/file> -alias <alias>
```

## Prüfen
```linux
# Public-Key
$ openssl x509 -noout -modulus -in <public-key-file>.crt | openssl md5

# Private Key
$ openssl rsa -noout -modulus -in <private-key-file>.key | openssl md5
```

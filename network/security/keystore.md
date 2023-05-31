# Keystore

## Konvertieren
### crt-Datei -> pkcs12
```linux
$ openssl pkcs12 \
          -export -in </path/to/cert/file> \
          -inkey <path/to/private/key/file> \
          -out </path/p12/key/file> 
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
$ keytool -importcert \
          -file <path/to/cert/file> \
          -keystore <path/to/jks/keystore/file> \
          -alias <alias>
```

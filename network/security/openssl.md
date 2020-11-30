# OpenSSL

## Generieren
### Erzeugen von Certificate Signing Requests (CSRs)
```linux
# Mit einem neuen Schlüssel
openssl req -out <csr>.csr -new -newkey rsa:2048 -nodes -keyout <private-key>.key

# Auf der Basis von einem vorhandenen Schlüssel

```
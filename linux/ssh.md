# SSH
Ein paar Notizen rund um SSH

## Wichtige Dateien

## Generieren von einem SSH-Schlüsselpaar
```
$ ssh-keygen -t rsa -b <keysize>
```

## Kopieren von einem Schlüssel
```
$ ssh-copy-id -i path/to/public/key user@host
```

## Login
```
$ ssh -i /path/to/private/key user@host
```

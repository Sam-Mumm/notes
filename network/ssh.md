# SSH
Ein paar Notizen rund um SSH

## Wichtige Dateien
| Datei | Bedeutung |
| --- | ---|
| `~/.ssh/authorized_keys` | öffentliche Schlüssel |

## Generieren von einem SSH-Schlüsselpaar
```
$ ssh-keygen -t rsa -b <keysize> -N <passwort> -f /path/to/dir/id_rsa
```

## Kopieren von einem Schlüssel
```
$ ssh-copy-id -i path/to/public/key user@host
```

## Login
```
$ ssh -i /path/to/private/key user@host
```

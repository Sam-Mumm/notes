# Vault

## Erstellen
```
$ ansible-vault create <file>.yml
```

## Syntax im Vault
Zu verwenden wie eine normale Variable Datei z.B.:
```
<variable>: <value>
```

## Verschlüsseln / Entschlüsseln
```
# Entschlüsseln
$ ansible-vault encrypt <file>.yml

# Verschlüsseln
$ ansible-vault decrypt <file>.yml
```

## Bearbeiten
```
$ ansible-vault edit <file>.yml
```

## Verwendung

### Passwortübergabe
```
# Übergabe des vault-Passworts als Datei
$ ansible-playbook -i hosts.ini site.yml --vault-password-file /pfad/zur/passwort/datei

# Abfragen des Passworts beim Aufruf
$ ansible-playbook -i hosts.ini site.yml --ask-vault-pass
```

# htaccess / htpasswd

## Basic Authentication
### htpasswd (Passwort-Datei)
**Generieren der Datei**
```
# Mit interaktiver Passwortabfrage 
$ htpasswd -c </path/to/file> <username> 

# Direkt von der Kommandozeile
$ htpasswd -bc </path/to/file> <username> <password> 
```

**Ergebnis**
```
jdoe:$apr1$CYtEbuvM$RJAnyd0neRc0883.hVnzP/
```


### htaccess
```
AuthType Basic
AuthName "Restricted Content"
AuthUserFile </path/to/htpasswd/file>
Require valid-user
```
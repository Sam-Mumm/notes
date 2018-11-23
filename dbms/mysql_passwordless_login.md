# MySQL - Passwortlose Anmeldung

Um für einen Benutzer die passwortlose Anmeldung an MySQL zu ermöglichen muss eine Datei mit dem Namen ``~/.my.cnf`` im Home-Verzeichnis des Benutzers erstellt werden.

## Inhalt der .my.cnf
```
[client]
host     = <hostname>
user     = <username>
password = <password>
socket   = /var/run/mysqld/mysqld.sock
database = <dbname>
```

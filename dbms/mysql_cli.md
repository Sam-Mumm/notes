# MySQL - Command Line Interface

## Anmeldung
```
$ mysql -u <Benutzer> -p <Password> -h <ocalhost|IP|Hostname> <Datenbank>
```

## Benutzerverwaltung
### Erstellen
```
mysql> GRANT ALL PRIVILEGES ON <dbname>.* TO '<username>'@'<localhost|IP|Hostname|%>' IDENTIFIED BY '************' WITH GRANT OPTION;
mysql> FLUSH PRIVILEGES;
```

## Datensicherung
### Backup
```
$ mysqldump -u <username> -p <Password> <dbname> > /path/to/dump/file.sql
```

### Restore
```
$ mysql -u <username> -p <Password> <dbname> < /path/to/dump/file.sql
```

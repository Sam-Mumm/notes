# MySQL-CLI-Befehle

## Anlegen von einem Benutzer / Setzen der Rechte für einen Benutzer
```
mysql> GRANT ALL PRIVILEGES ON <dbname>.* TO '<username>'@'<localhost|IP|Hostname|%>' IDENTIFIED BY '************' WITH GRANT OPTION;
mysql> FLUSH PRIVILEGES;
```

## Backup/Restore einer Datenbank
### Backup
```
$ mysqldump -u <username> -p <Password> <dbname> > /path/to/dump/file.sql
```

### Restore
```
$ mysql -u <username> -p <Password> <dbname> < /path/to/dump/file.sql
```

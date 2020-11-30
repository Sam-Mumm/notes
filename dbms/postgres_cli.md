# Postgres - Command Line Interface

## Anmeldung
### Als root-Benutzer
```
su - postgres
psql
```

### Als nicht-privilegierter Benutzer
```
psql -U <Benutzer> -h <localhost|IP|Hostname> <Datenbankname>
```

## Navigation in der Datenbank-CLI
Eine Liste der grundlegenden Befehle, eine vollständige Liste der Befehle sind über den Befehl <code>\?</code> abrufbar.

| Befehl | Beschreibung|
| --- | --- |
| <code>\?</code> | Hilfe |
| <code>\q</code> | Verlassen des Postgres-Prompt |
| <code>\l</code> | Auflisten der Datenbanken |
| <code>\c  Datenbankname </code> | Verbinden zur übergebenen Datenbank |
| <code>\dt</code> | Auflisten der Tabellen der Datenbank |

## Benutzerverwaltung
### Erstellen von Benutzern
```
CREATE USER <username> with encrypted password '<password>';
```


### Setzen von Berechtigungen
#### ... auf Datenbank-Ebene
```
GRANT <permission> privileges on database <database> to <username>;
```

Auswahl an gültigen Werten für `permission`:
  - `all`
  - `create`
  - `connect`

#### ... auf Tabellen-Ebene
```
GRANT <permission> privileges on table <table> to <username>;
```

Auswahl an gültigen Werten für `permission`:
  - `select`
  - `insert`
  - `delete`
  - `update`

## Backup und Restore
Die folgende Befehle müssen auf der Kommandozeile des Hosts d.h. nicht in der Datenbank ausgeführt werden:

### Restore
Für ein Restore einer Datenbank muss die Datenbank im Datenbank-Server bereits existieren.
```
$ PGPASSWORD = '*********' && psql -h <host> -U <User> <Database> < /path/to/dump/file.sql 
```

### Backup
```
$ PGPASSWORD = '*********' && pg_dump --no-owner -h <host> -U <User> <Database> > /path/to/dump/file.sql 
```

## Passwortloser Login
**Datei:** ~/.pgpasss
```
<Host>:<Port>:<Database>:<User>:<Password>
localhost:5432:mydatabase:jdoe:geheim!
```
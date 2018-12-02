# Postgres - Command Line Interface

## Anmeldung
### Als root-Benutzer
```
su - postgres
psql
```

### Als nicht-privilegierter Benutzer
```
psql -U <Benutzer> -h <ocalhost|IP|Hostname> <Datenbankname>
```

### Navigation in der Datenbank
Eine Liste der grundlegenden Befehle, eine vollständige Liste der Befehle sind über den Befehl <code>\?</code> abrufbar.

| Befehl | Beschreibung|
| --- | --- |
| <code>\?</code> | Hilfe |
| <code>\q</code> | Verlassen des Postgres-Prompt |
| <code>\l</code> | Auflisten der Datenbanken |
| <code>\c  Datenbankname </code> | Verbinden zur übergebenen Datenbank |
| <code>\dt</code> | Auflisten der Tabellen der Datenbank |




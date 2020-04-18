# CLI

#### chmod - Dateirechte ändern
```
chmod [-R] <Rechte> <Datei/Verzeichnis>
```
| Wert | Bedeutung |
| -- | -- |
| 1 | Ausführen (x) |
| 2 | Schreiben (w) |
| 4 | Lesen (r) |

---

#### Cronjob
![cronjob](cronjob.png) 
##### Editieren der Cronjobs (für Benutzer *user*)
```
crontab -e [-u <user>]
```

##### Anzeigen der Cronjobs (für Benutzer *user*)
```
crontab -l [-u <user>]
```

---

#### cURL
```
curl <parameter> <URL>
```

|<Optionen>| Erklärung|
| --- | --- |
| -u<User>:<Password> | Benutzer und Passwort für die Authentifikation |
| -X <POST|GET> | Typ des Requests |
| -H <Header> | Zu übertragender Header |
| -d<Payload> | Zu übertragende Daten (@<path/to/file> für Dateien) |
| -n | Nutzung der `.netrc` für die Authentifikation (wird im Home-Verzeichnis vom Benutzer gesucht) |

##### Aufbau .netrc
```
machine <Hostname|FQDN> login <user> password <password>
```

---

#### diff
##### Vergleich von zwei Verzeichnissen
```
diff -i -r --brief /path/to/dir1 /path/to/dir2
```

---

#### Mail versand
```
echo "content" | mailx -s "Subject" -r sender@example.com recipient1@example.com[,recipient2@example.com] 
```

---

#### netstat
```
$ netstat <Optionen>
```

|<Optionen>| Erklärung|
| --- | --- |
|``t``| |
|``u``| |
|``l``| |
|``p``| |
|``e``| |
|``n``| numerische Adressen |

---
#### find - Dateien und Verzeichnisse finden
##### Nach Dateien mit dem Namen suchen
```
find [/path/to/directory] -iname [Datei]
```
---
#### rsync - Synchronisieren von Dateien und Verzeichnissen
##### Sync' anhand einer Liste
```
rsync -aSvuc --recursive --files-from=</path/to/backup.list> </path/to/source> </path/to/target> 
```

**Anmerkung:** Die Einträge in der `backup.list` müssen relativ zu dem Verzeichnis im rsync-Aufruf sein

---
#### PDF-Dateien manipulieren
**benötigtes Paket:** pdftk

##### Zusammenführen
```
pdftk <date1.pdf> <date2.pdf> <date3.pdf>  cat output <ausgabe.pdf>
```

##### Trennen

---
#### screen - Prozesse in den Hintergrund legen
| Befehl | Erklärung |
| -- | -- |
| ``screen`` | Screen starten |
| ``screen -list`` | laufende Screen-Session auflisten |
| ``screen -r <PID>`` | Screen-Session fortsetzen |
| [Strg] + a -> [Strg] + d | Screen-Session in den Hintergrund legen |



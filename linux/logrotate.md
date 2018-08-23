# Logrotate

## Aufruf
```
logrotate -s /path/to/statusfile /path/to/config/file
```

## Parameter
Eine vollständige Liste ist per ``man logrotate`` zu erhalten:
 * **size:** Dateigröße bei der rotiert wird  
 * **rotate:** Anzahl der Dateien die maximal vorgehalten werden
 * **create:** Rechte/Benutzer/Gruppe mit der die neue Logdatei erstellt wird
 * **prerotate:** Skript(e) die vor dem rotieren ausgeführt wird/werden
 * **postrotate:** Skript(e) die nach dem rotieren ausgeführt wird/werden
 * **dateext:** Erweitert die rotierte Datei um ein Datum
 * **truncatecopy:** Kopiert und Leert die Datei statt sie umzubenennen

## Beispiel
```
/path/to/log/file {
	rotate 5
	size=4M
	create 660 [user] [group]
	prerotate
		/path/to/script
	endscript
}
```

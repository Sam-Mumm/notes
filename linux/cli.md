# CLI

### chmod - Dateirechte ändern
```
chmod [-R] <Rechte> <Datei/Verzeichnis>
```
| 1 | Ausführen (x) |
| 2 | Schreiben (w) |
| 4 | Lesen (r) |


### find - Dateien und Verzeichnisse finden
#### Nach Dateien mit dem Namen suchen
```
find [/path/to/directory] -iname [Datei]
```

### screen - Prozesse in den Hintergrund legen
| ``screen`` | Screen starten |
| ``screen -list`` | laufende Screen-Session auflisten |
| ``screen -r <PID>`` | Screen-Session fortsetzen |
| [Strg] + a -> [Strg] + d | Screen-Session in den Hintergrund legen |

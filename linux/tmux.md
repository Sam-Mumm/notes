# tmux

## Allgemeine Nutzung
### Tastaturbelegung
Jeder Befehl beginnt mit dem drücken von <kbd>Strg</kbd>+<kbd>B</kbd> gefolgt von einem der folgenden Tasten

| Taste | Ergebnis |
| --- | --- |
| <kbd>C</kbd> | Erstellt ein neues Fenster |
| <kbd>&</kbd> | Schließt das aktuelle Fenster |
| <kbd>"</kbd> | Teilt das Panel horizontal |
| <kbd>%</kbd> | Teilt das Panel vertikal |
| <kbd>n</kbd> | nächstes Fenster |
| <kbd>p</kbd> | vorheriges Fenster  |
| <kbd>q</kbd> <kbd>0</kbd> ... <kbd>9</kbd> | Wechsel zum Fenster mit der angegeben Nummer|


## Aufrufe
### Shared Sessions

#### Neue Session erstellen
```
$ tmux new -s <name>
```

#### Verbinden zu einer vorhandenen Session
```
$ tmux attach -t <name>
```

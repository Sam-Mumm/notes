# Docker



## Nutzung
#### Grundbefehl
```
$ docker <optionen>
```

#### Optionen
Eine vollständige Liste der verfügbaren Optionen ist auf der Docker-Befehle ist [hier](https://docs.docker.com/engine/reference/commandline/cp/) hier zu finden.
Aber hier eine Auswahl der Befehle die man regelmäßig benötigt

|Optionen|Kekse|
|---|---|
| `cp <src>` <dest> | Kopieren einer Datein in oder aus einem Container, der Container wird hierbei referenziert mittels ``<Image_ID>:<path/to/file>`` |
| `exec -it <Image-ID|Name> <Command>` | Ausführen von ``<Command>`` in einem laufenden Container |
| `pull <Name>` | Herunterladen von einem Image |
| `ps [-a]` | Anzeigen (aller) der laufenden Container |
| `rm <Container-ID|Name>` | Löschen von einem Image |
| `rmi <Image-ID|Name>` | Löschen von einem Image |
| `run <Image>[Tag]` | Starten von einem Container |
| `search <Muster> [URL]` | Suche nach Docker Images die ``<Muster>`` enthalten |
| `tag <Image> <Name>:<Tag>` | Ändern des Tags eines Images  |


## Erstellen von Images

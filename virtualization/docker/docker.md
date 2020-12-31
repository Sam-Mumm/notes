# Docker

## Nutzung
#### Grundbefehl
```
$ docker <optionen>
```

#### Optionen
Eine vollständige Liste der verfügbaren Optionen ist auf der Docker-Befehle ist [hier](https://docs.docker.com/engine/reference/commandline/cp/) zu finden.
Eine Auswahl der Befehle:

|Optionen|Kekse|
|---|---|
| `cp <src> <dest>` | Kopieren einer Datein in oder aus einem Container, der Container wird hierbei referenziert mittels `<Image_ID>:<path/to/file>` |
| `pull <Name>` | Herunterladen von einem Image |
| `ps [-a]` | Anzeigen (aller) laufenden Container |
| `rm <Container-ID|Name>` | Löschen von einem Image |
| `rmi <Image-ID|Name>` | Löschen von einem Image |
| `run <Image>[Tag]` | Starten von einem Container |
| `search <Muster> [URL]` | Suche nach Docker Images die `<Muster>` enthalten |
| `tag <Image> <Name>:<Tag>` | Ändern des Tags eines Images  |


## Erstellen von Images
#### Befehle


#### Beispiele


## Nützliches
### Alle Tags von einem Image
```
$ wget -q https://registry.hub.docker.com/v1/repositories/debian/tags -O -  | sed -e 's/[][]//g' -e 's/"//g' -e 's/ //g' | tr '}' '\n'  | awk -F: '{print $3}'
```

### Befehle
#### Arbeiten in einem Container
```
$ docker exec -ti <Container_Name> <Binary_im_Container>
```

#### Starten von einem Docker-Container
##### Im Hintergrund
```
$ docker run -d --name <Container_Name> <Image_Name>:<Tag> <Binary_im_Container>
```
*Hinweis:* Wenn nur ein Container am leben gehalten werden soll, kann oft auch `sleep inf` als Befehl verwendet werden

##### Im Vordergrund
```
$ docker run --name <Container_Name> -it <Image_Name>:<Tag> <Binary_im_Container>
```

# pip

## Installation
Zwei Optionen:
- Über den Paketmanager der Distribution
- ``curl https://bootstrap.pypa.io/get-pip.py -o get-pip.py``

## Verwendung
Neben den unten angeführten Beispielen, kann in Python 3 auch die Syntax:
```
$ python3 -m pip install <command>
```
verwendet werden

#### Installation
##### Installieren von einem expliziten Paketen
```
$ pip install [--proxy=https://user@<proxy>:port] <package>
```

##### Einlesen von Paketlisten
```
$ pip install [--proxy=https://user@<proxy>:port] -r requirements.txt
```
---
#### Generieren von Paketlisten
```
$ pip freeze -l
```

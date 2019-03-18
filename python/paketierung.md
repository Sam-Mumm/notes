# paketierung

## Voraussetzungen
### Pakete 
Folgende Pakete werden benötige um Python-Pakete generieren zu können:
 * setuptools
 * wheel
 * twine (Optional)

## minimale Struktur
```
README.md
LICENSE
setup.py
example_pkg
  └─ __init__.py
```

## Dateien
### setup.py
#### Pflichtfelder
Die folgende Parameter sind Pflichtfelder:
 * name
 * version

#### Beispiel
```
from setuptools import setup, find_packages

setup(
    name = 'wiki',
    version = '1.0.0',
    url = 'https://github.com/Sam-Mumm/wiki.git',
    author = 'Dan',
    author_email = 'author@gmail.com',
    description = 'Description of my package',
    packages = find_packages(),
    install_requires = ['flask', 'matplotlib >= 1.5.1'],
)
```

## Verwendung
### Pakete erzeugen
Aus dem gleichen Verzeichnis in dem sich die `setup.py` befindet den Befehl:
```
$ python3 setup.py sdist bdist_wheel
```
ausführen. Die Pakete befinden sich anschließend in dem Verzeichnis `dist/`

## Hochladen der Pakete
### Mit twine
```
$ python3 -m twine upload --repository-url https://test.pypi.org/legacy/ dist/*
```

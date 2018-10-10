# Paketverwaltung

## Verwaltung von Software (Paketen)

| Aufgabe | apt | yum | zypp(er) | pacman |
| -- | -- | -- | --| -- |
| Installation von einem Paket aus einem Repository | ``apt-get install <Package>`` | ``yum install <Package>`` | ``zypper install <Package>`` | ``pacman -S <Package>`` |
| Installation von einem lokalen Paket | ``dpkg -i <Package>`` | ``ỳum localinstall <Package>`` | ``zypper install <Package>`` | ``pacman -U <Package>`` |
| Update von einem bereits installierten Paket | ``apt-get install <Package>`` | ``yum update <Package>`` | ``zypper update -t package <Package>`` | ``pacman -S <Package>`` |
| Deinstallieren von einem Paket | ``apt-get remove <Package>`` | ``yum erase <Package>`` | ``zypper remove <Package> | ``pacman -R <Package>`` |


## Aktualisieren
| Aufgabe | apt | yum | zypp(er) | pacman |
| -- | -- | -- | -- | -- |
|Aktualisieren des Paketcaches |``apt-get update``|``yum check-update``|``zypper refresh``| ``pacman -Sy`` |
|Aktualisieren von dem Betriebssystem|``apt-get upgrade``|``yum update``|``zypper update``| ``pacman -Su`` |
|Prüfen aller Abhängigkeiten|``apt-get check``| *<Not supported>* | *<Not supported>* | *<Not supported>* |
|Reparieren von Abhängigkeitsproblemen|``apt-get -f install``| *<Not supported>* | *<Not supported>* | *<Not supported>* |


## Suchen
| Aufgabe | apt | yum | zypp(er) | pacman |
| -- | -- | -- | --| -- |
|Suche nach einem Paket bei seinem Namen|``apt-cache search <Package>``|``yum list <Package>``|``zypper search <Package>``| ``pacman -Ss <Package>`` |
|Suche nach einem Paket mit einem String|``apt-cache search <String>``|``yum search <String>``|``zypper search -t pattern <String>``| ``pacman -Ss <String>`` |
|Suche nach einem Paket anhand einer beinhalten Datei|``apt-file search <File>``|``yum provides <File>``|``zypper wp <File>``| ``pacman -Qo <File>`` |
|Auflistung aller installierten Pakete|``dpkg -l``|``yum list installed``|``zypper search -is``| ``pacman -Q <File>`` |

## Repository Verwaltung
| Aufgabe | apt | yum | zypp(er) | pacman |
| -- | -- | -- | -- | -- |
|Auflisten der eingebundenen Repositories|``cat /etc/apt/sources.list``|``yum repolist``|``zypper repos``| ``cat /etc/pacman.conf`` |
|Hinzufügen von einem Repository|Bearbeiten der ``/etc/sources.list``|Hinzufügen der Repo-Definition in das Verzeichnis ``/etc/yum.repos.d`` | ``zypper addrepo <Path_Name>``| Bearbeiten der ``/etc/pacman.conf`` |
|Entfernen von einem Repository|Bearbeiten der ``/etc/sources.list``|Hinzufügen der Repo-Definition in das Verzeichnis ``/etc/yum.repos.d``|``zypper removerepo <Name>| Bearbeiten der ``/etc/pacman.conf`` |

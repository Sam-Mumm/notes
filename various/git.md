# git

## Konfiguration
### Abfragen von Einstellungen
```
$ git config --<global|system> --get <Setting>
```

### Beispiele
#### Remote-git-Repository
##### Abfragen
```
# Schluessel: remote.origin.url
# Alternative
$ git remote -v
```

##### Setzen
```
$ git remote set-url <URL> 
```

#### Proxy konfigurieren
##### Setzen
```
$ git config --global http.proxy http://user:password@proxy.example.com:<port>
$ git config --global https.proxy http://user:password@proxy.example.com:<port>
```

##### Entfernen
```
$ git config --global --unset http.proxy
$ git config --global --unset https.proxy
```

## Stages
![](.//git.png) 


## Cheat Sheet

## Beispiele
### Cherrypicking
```
$ git cherry-pick -x 32a8e28
Finished one cherry-pick.
[master b5285e9] bugfix (cherry picked from commit 32a8e28)

$ git push
```

### Partielles Merge von einem anderen Branch (develop -> master)
```
$ git branch
  master
* develop
$ git checkout master
$ git checkout develop /path/to/files/to/merge
$ git add *
$ git commit -m "..."
$ git push
```

### Lösen von Merge-Konflikten aus Feature-Branchs
```
# Holen vom letzten Stand des Masters
$ git checkout master
$ git pull origin master

# Wechseln zum Feature-Branch
$ git checkout feature/tool
$ git pull origin feature/tool

# Ermitteln der Mergekonflikte 
$ git merge master
$ git status

# Änderung versionieren
git add <file>
git commit -m "<message>"
git pushin origin feature/tool
```

# git
## Proxy konfigurieren
### Abfragen
```
$ git config --global --get http.proxy
```

### Setzen
```
$ git config --global http.proxy http://user:password@proxy.example.com:8080
```

### Entfernen
```
$ git config --global --unset http.proxy
```


## Cherry picking
```
$ git cherry-pick -x 32a8e28
Finished one cherry-pick.
[master b5285e9] bugfix (cherry picked from commit 32a8e28)

$ git push
```


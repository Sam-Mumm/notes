# Konfigurationsdatei - ansible.cfg

## Definitionen
Die ``ansible.cfg`` kann über die folgenden Wege definiert werden
  - als Datei im Verzeichnis: /etc/ansible.cfg
  - als Datei im Verzeichnis: ~/.ansible.cfg
  - als Datei im Projektverzeichnis
  - als Umgebungsvariable: ANSIBLE_CONFIG

## Dokumentation
Eine vollständige Liste aller Parameter für die ansible.cfg ist in der [Dokumentation](https://docs.ansible.com/ansible/2.4/intro_configuration.html) zu finden

## Beispiel
```
[defaults]
# relativer Pfad zur Inventory Datei
inventory = inventory/hosts

# Benutzer für den remote Login
remote_user = root

# Art des Caching
fact_gathering = smart

# Pfad zu den Cachefiles
fact_caching_connection = ~/.ansible/fact_cache

# Lebensdauer der gecachten Daten
fact_caching_timeout = 86400

# Ablageort der retry-Dateien
retry_files_save_path = ~/.ansible/retry-files

# relativer Pfad zu den Rollen
roles_path = roles
```


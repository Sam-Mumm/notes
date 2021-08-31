# Collections

## Aufbau
TBD

## Entwicklung
### Anlegen und Struktur
**Erstellen**
```
ansible-galaxy collection init <namespace>.<collection_name>
```

**Struktur**
```
<namespace>
 └─ <collection_name>
     ├─ docs
     ├─ galaxy.yml
     ├─ plugins
     │   └── README.md
     ├─ README.md
     └─ roles
```

### Build-Prozess
**Bauen**
Der Bauprozess besteht aus dem hinzufügen einiger Metadaten sowie packen der Daten als tar.gz
```
cd <namespace>
ansible-galaxy collection build <collection_name>
```

**Veröffentlichen**


## Verwendung

### Installieren
Die Installation erfolgt durch das auspacken in das in der `ansible.cfg` konfigurierte Verzeichnis, per Default `~/.ansible/collections/ansible_collections`

#### Fremdquellen



#### direkt
```
ansible-galaxy collection install <archivfile>.tar.gz
```

### Einbindung

#### ansible.cfg
```ini
[defaults]
collections_paths = ~/.ansible/collections:/usr/share/ansible/collections
```

#### Playbook



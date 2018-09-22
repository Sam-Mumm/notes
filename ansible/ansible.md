# Ansible - Cheat Sheet

Eine lose Sammlung an Codefragmenten ohne Anspruch auf vollständigkeit und/oder Korrektheit

## Grundgerüst für Playbooks
```
- hosts: <groupname> 
  become: yes
  become_user: <username>
  vars:
    <variable1>: <value1>
    <variable2>: <value2>
    ...
  pre_tasks:
    - <task_1>
      <task_2>
      ...
  tasks:
    - <task_1>
      <task_2>
      include: tasks.yaml
      ...
  post_tasks:
    - <task_1>
      <task_2>
      ...
  roles:
    - common
    - { role: common, when: month=may }

```

## Tasks
```
  tasks
    - name <Beschreibung>
      <Command>: <Options>
```

## Verzeichnisstruktur für Rollen
```
hosts.ini
playbook.yml
host_vars
roles/
  ├─ defaults
  │     └─ main.yml
  ├─ files  
  ├─ handlers
  │     └─ main.yml
  ├─ meta
  │     └─ main.yml
  ├─ tasks
  │     └─ main.yml
  ├─ templates
  └─ vars
        └─ main.yml
```

Erstellen einer Rollen mit: 
```
  $ ansible-galaxy init <rollenname>
```

## Inventory
```
[groupname]
<hostname>
<fqdn> <variable1>=<value1> <variable2>=<value2>
```

## Variablen
Variablen können definiert werden:
  * im Playbook (Schlüsselwort vars:)
  * in der Datei: ``/host_vars/<hostname>.yaml`` für eine Host
  * in der Datei  ``/host_vars/<groupname>.yaml`` für alle Mitglieder der Gruppe <groupname> im Inventory

#### Zugriff
  * ``{{var}}``
  * ``{{var.key}}``
  
#### Filter
##### lookup
| Filter | Ergebnis |
| --- | --- |
|<code>{{ lookup('env','HOME') }}</code>| Abfragen einer Umgebungsvariable |
|<code>{{ lookup('template', './template.tmpl.j2') }}</code>| Parsen einer Templatedatei |


##### Mengen
| Filter | Ergebnis |
| --- | ---
| <code> {{ list1 \| union(list2) }} </code> | liefert die Vereinigung beider Listen |
| <code> {{ list1 \| difference(list2) }}  </code> | liefert alle Elemente aus Liste 1 die nicht in Liste 2 sind (list1 ohne list2) |
| <code> {{ list1 \| intersect(list2) }}  </code> | liefert die Schnittmenge beider Listen |
| <code> {{ list1 \| unique }} </code> | liefert eine Liste ohne doppelten Werte |

## Aufruf
```
# Aufruf
$ ansible-playbook -i hosts.ini playbook.yml <options>
```
| <Option> | Beschreibung
| --- | ---
| ``--private-key=/path/to/ssh/private/key`` | Privaten SSH-Key übergeben |
| ``--ask-pass`` | Fragen nachdem User-Passwort
| ``--ask-becom-pass`` | Frage nach dem sudo-Passwort |
| ``--ask-vault-pass`` | Frage nach dem vault-Passwort |
| ``--vault-password-file=/path/to/password/file`` | Pfad zur Passwort-Datei (Passwort im Klartext | 
| ``--become-user <Username>`` | Definieren zu welchem Benutzer gewechselt werden soll |
| ``--extra-vars "version=42"`` | Übergeben von Variablen |

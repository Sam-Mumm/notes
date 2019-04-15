# Ansible

Eine lose Sammlung an Codefragmenten ohne Anspruch auf vollständigkeit und/oder Korrektheit

## Inventory
```
[groupname]
<hostname>
<fqdn> <variable1>=<value1> <variable2>=<value2>
```

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
      include_task: tasks.yaml
      ...
  post_tasks:
    - <task_1>
      <task_2>
      ...
  roles:
    - common
    - { role: common, when: month=may }
    - role: common
      tags: ['never', 'common']
```

### Struktur eines Tasks
```
  tasks
    - name <Beschreibung>
      <Command>: <Options>
      tags: ['<tag1>', '<tag2>', ...]
```

## Tags
Mit Label makiert werden können:
* Tasks
* Rollen
* include_tasks

Einige Tags besitzen besondere Eigenschaften:
* **always:** Die Tasks werden immer ausgeführt und können per <code>--skip-tags \<tagname></code> übersprungen werden
* **never:** Die Tasks werden nur ausgeführt wenn sie per <code>--tags \<tagname></code> explizit genannt werden

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

## Variablen
### Orte
Variablen können definiert werden:
  * im Playbook (Schlüsselwort vars:)
  * in der Datei: ``/host_vars/<hostname>.yaml`` für eine Host
  * in der Datei  ``/host_vars/<groupname>.yaml`` für alle Mitglieder der Gruppe <groupname> im Inventory

### Datentypen
#### Variable
```
answer: 42
hello: "good bye"
```

#### Liste
```
user:
  - Alice
  - Bob
  - Trudy
```

#### Dictionary  
```
interface:
  ip: "192.168.1.1"
  netmask: "255.255.255.o"
  gateway: "192.168.1.0"
```

#### geschachtelte Variablen
```

```


### Zugriff
Die elementaren Zugriffsarten sind:
  * **Variable:** <code>{{var}}</code>
  * **Liste:** <code>{{var[0]}}</code>
  * **Dictionary:** <code>{{var.key}}</code>
  
### Filter
#### **lookup**
| Filter | Ergebnis |
| --- | --- |
|<code>{{ lookup('password', '/tmp/passwordfile length=20 chars=ascii_letters,digits') }}</code>| Generieren von einem Passwort |
|<code>{{ lookup('env','HOME') }}</code>| Abfragen einer Umgebungsvariable |
|<code>{{ lookup('template', './template.tmpl.j2') }}</code>| Parsen einer Templatedatei |
|<code>{{ lookup('url', 'http://example.com/index.html') }}</code>| Laden des Inhalts von einem Dokument per HTTP-Anfrage |


#### **Mengen**
| Filter | Ergebnis |
| --- | ---
| <code> {{ list1 \| union(list2) }} </code> | liefert die Vereinigung beider Listen |
| <code> {{ list1 \| difference(list2) }}  </code> | liefert alle Elemente aus Liste 1 die nicht in Liste 2 sind (list1 ohne list2) |
| <code> {{ list1 \| intersect(list2) }}  </code> | liefert die Schnittmenge beider Listen |
| <code> {{ list1 \| unique }} </code> | liefert eine Liste ohne doppelten Werte |


### Implizite Variable
| Variable | Beschreibung |
| groups | Dictionary aller Inventory-Gruppen (einschließlich der Hosts) |
| hostsvars | Hostvariablen aller Inventory Hosts (einschließlich der facts) |


### Rangordnung
(von niedrigster zur höchsten Priorität) 

1. extra vars (always win precedence)
2. include params
3. role (and include_role) params
4. set_facts / registered vars
5. include_vars
6. task vars (only for the task)
7. block vars (only for tasks in block)
8. role vars (defined in role/vars/main.yml)
9. play vars_files
10. play vars_prompt
11. play vars
12. host facts / cached set_facts
13. playbook host_vars/*
14. inventory host_vars/*
15. inventory file or script host vars
16. playbook group_vars/*
17. inventory group_vars/*
18. playbook group_vars/all
19. inventory group_vars/all
20. inventory file or script group vars
21. role defaults
22. command line values (eg “-u user”)


## Aufruf
```
# Aufruf
$ ansible-playbook -i hosts.ini playbook.yml <options>
```
| <Option> | Beschreibung
| --- | ---
| ``--private-key=/path/to/ssh/private/key`` | Privaten SSH-Key übergeben |
| ``--ask-pass`` | Fragen nachdem User-Passwort | 
| ``--ask-become-pass`` | Frage nach dem sudo-Passwort |
| ``--ask-vault-pass`` | Frage nach dem vault-Passwort |
| ``--vault-password-file=/path/to/password/file`` | Pfad zur Passwort-Datei (Passwort im Klartext | 
| ``--become-user <Username>`` | Definieren zu welchem Benutzer gewechselt werden soll |
| ``--extra-vars "<variable_1>=<wert_1> <variable_2>=<wert_2> ... <variable_n>=<wert_n>"`` | Übergeben von Variablen |
| ``--tags <tag1> <tag2> <tag3> ... `` | Ausführen der Tasks die mit den übergebenen Tags markiert sind |
| ``--skip-tags <tag1> <tag2> <tag3> ... `` | Überspringen der Tasks die mit den übergebenen Tags gelabeld sind |

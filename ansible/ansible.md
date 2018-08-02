# Ansible - Cheat Sheet

Eine lose Sammlung an Codefragmenten ohne Anspruch auf vollständigkeit und/oder Korrektheit

## Grundgerüst
```
- hosts: all
  become: yes
  become_user: apache
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

## Verzeichnisstruktur für Rollen
```
hosts.ini
playbook.yml
roles/
  ├── defaults
  │     └── main.yml
  ├── files
  ├── handlers
  │     └── main.yml
  ├── meta
  │     └── main.yml
  ├── tasks
  │     └── main.yml
  ├── templates
  └── vars
        └── main.yml
```

Erstellen einer Rollen mit: 
```
  $ ansible-galaxy init <rollenname>
```

## Aufruf
```
# Übergeben eines privaten Schlüssels
$ ansible-playbook -i hosts.ini playbook.yml <options>
```
| <Option> | Beschreibung
| --- | ---
| ``--private-key=/path/to/ssh/private/key`` | Privaten SSH-Key übergeben |
| ``--ask-pass`` | Fragen nachdem User-Passwort
| ``--ask-becom-pass`` | Fragen nachdem sudo-Passwort |
| ``--become-user <Username>`` | Definieren zu welchem Benutzer gewechselt werden soll |
| ``--extra-vars "version=42"`` | Übergeben von Variablen |



# Codeschnipsel
Alle nachfolgenden Codefragmente basieren auf ansible in der Version 2.5 und beziehen sich auf ein Inventoryfile mit diesem Inhalt:

```
[web]
ServerA
ServerB
ServerC
```


## Datei Operationen
### Template-Task

-----------------

### Kopieren-Task
```
- hosts: all
  tasks:
    - name: Copy local file foobar to /tmp/helloworld on Remote
      copy:
        src: "foobar"
        dest: /tmp/helloworld
        owner: root
        group: root
        mode: 0644
        backup: yes
    - name: Copy file /tmp/helloworld from remote to /tmp/foobar on local
      fetch:
        src: /tmp/helloworld
        dest: /tmp/foobar
        flat: yes
```
**Modul-Dokumentation:**
- **Copy:** https://docs.ansible.com/ansible/2.5/modules/copy_module.html
- **Fetch:** https://docs.ansible.com/ansible/2.5/modules/fetch_module.html
-----------------

### File-Task
```
- hosts: all
  tasks:
    - name: create a link from /etc/passwd to /tmp/passwd
      file:
        src: /etc/passwd
        dest: /tmp/passwd
        state: link 

    - name: create a file /tmp/foobar
      file:
        path: /tmp/foobar
        state: touch
        owner: dsteffen
        group: dsteffen
        mode: 0644
```
**Modul-Dokumentation:** https://docs.ansible.com/ansible/2.5/modules/file_module.html#file-module

-----------------

## Schleifen
### with_items
**Modul-Dokumentation:** https://docs.ansible.com/ansible/2.5/plugins/lookup/items.html

```
- hosts: all
  vars:
    - liste
        - Aa
        - Bb
        - Cc
    - users:
        - { name: 'jdoe', group: 'ssh' }
        - { name: 'pmustermann', group: 'user' }
  tasks:
    - name: Iterate through Variable/Inventory
      debug:
        msg: "Hosts: {{ item }}"
      with_items: "{{ groups['web'] }}"
    - name: Iterate through list of single Elements
      debug:
        msg: "{{item}}"
      with_items: "{{liste}}"
    - name: Iterate through list of dictionaries
      debug:
        msg: "{{item.name}} in Group {{item.group}}"
      with_items: "{{liste}}"

```

### with_lines

-----------------

## Lookups
### Generate Passwords

### CSV-Dateien

-----------------

## Debug
```
- hosts: all
  tasks:
    - name: Display Hello World
      debug:
        msg: "Hello World"
```
**Modul-Dokumentation:** https://docs.ansible.com/ansible/2.5/modules/debug_module.html
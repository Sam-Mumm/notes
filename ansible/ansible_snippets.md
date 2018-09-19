# Codeschnipsel
Alle nachfolgenden Codefragmente basieren auf ansible in der Version 2.5

## Template-Task

## Copy-Task
```
- hosts: all
  tasks:
    - name: Copy file foobar to /tmp/helloworld
      copy:
        src: "foobar"
        dest: /tmp/helloworld
        owner: root
        group: root
        mode: 0644
        backup: yes
```
**Modul-Dokumentation:** https://docs.ansible.com/ansible/2.5/modules/copy_module.html

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
#### Iteration über die Hosts einer Inventory-Gruppe
**Hosts.ini**
```
[web]
ServerA
ServerB
ServerC
```

**sites.yml**
```
- hosts: all
  tasks:
    - name: Iterate through Hosts in the web Group
      debug:
        msg: "Hosts: {{ item }}"
      with_items: "{{ groups['web'] }}"
```

### with_lines

-----------------

## Lookups
### Generate Passwords

### Dateien

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

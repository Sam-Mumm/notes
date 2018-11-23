# Codeschnipsel
Alle nachfolgenden Codefragmente basieren auf ansible in der Version 2.5 und beziehen sich auf ein Inventoryfile mit diesem Inhalt:

```
[web]
ServerA
ServerB
ServerC

[logserver]
ServerD
```


## Datei Operationen
### Template-Task
```
- hosts: all
  tasks:
    - name: Copy template to the home-directory of the user
      template:
        src: "index.html.j2"
        dest: "/var/www/html/index.html"
        owner: apache
        group: user
        mode: '0644'
```

 - **Modul-Dokumentation:**	  https://docs.ansible.com/ansible/2.5/modules/template_module.html

 - **Notizen:**
     - Dateien die als Templates genutzt werden, sollten auf "*.j2" enden
     - In Rollen werden Templates im Ordner <code>templates</code> gesucht
     - Templates werden per jinja2 geparst

-----------------

### Kopieren von Dateien
**Datei:** group_vars/all.yml
```
content: ""
```

**Playbook**
```
- hosts: ServerA
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
        
    - name: Get Content of file /tmp/barfoo
       slurp:
         src: "/tmp/barfoo"
       register: tmp
    - name: store variable to content
      set_fact:
        content: "{{tmp.content}}"  


- hosts: ServerB
  tasks:
    - name: Create file /tmp/helloworld with content of /tmp/barfoo
      copy:
        dest: /tmp/helloworld
        content: "{{content}}"                 
```
**Modul-Dokumentation:**
- **Copy:** https://docs.ansible.com/ansible/2.5/modules/copy_module.html
- **Fetch:** https://docs.ansible.com/ansible/2.5/modules/fetch_module.html
- **slurp:** https://docs.ansible.com/ansible/2.5/modules/slurp_module.html
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


### HashiCorp Vault
**Voraussetzung: ** Setzt das Python-Modul **hvac** voraus
```
- hosts: localhost
  vars:
    path_to_secret: "secret/message:value"
    vault_token: "2mDlFNUawn7tDGiTP7hTPCSP"
    vault_server: "https://vaultserver.example.com:8200"
    cacert_path: "/etc/vault/fullchain.pem"
    password: "{{ lookup('hashi_vault', 'secret={{ path_to_secret }} token={{ vault_token }} url={{ vault_server }} cacert={{ cacert_path }}') }}"
  tasks:
    - name: Output Password
      debug:
        msg: "{{password}}"
```
**Modul-Dokumentation:** https://docs.ansible.com/ansible/2.5/plugins/lookup/hashi_vault.html

-----------------

## Linux
### Benutzer und Gruppen
```
- hosts: all
  vars:
    pwd: "secret"
  tasks:
    - name: Create group foobar
      group:
        name: "foobar"
        gid: 4711
        state: present

    - name: Create User jdoe
      user:
        name: "jdoe"
        group: "foobar"
        home: /home/jdoe
        shell: /bin/bash
        password: "{{ pwd | password_hash('sha512') }}"
```
**Modul-Dokumentation:**
- **Group:** https://docs.ansible.com/ansible/2.5/modules/group_module.html
- **User:** https://docs.ansible.com/ansible/2.5/modules/user_module.html


### Startscripte

-----------------

## sonstige Module
### Variable überprüfen
```
- hosts: all
  tasks:
    - name: Verify the values of variables
      assert:
        that:
          - "port >= 1"
          - "port <= 65535"
      msg: "Variable port must be between 1 and 65535"
```
**Modul-Dokumentation:** https://docs.ansible.com/ansible/2.5/modules/assert_module.html

### Debug
```
- hosts: all
  vars:
    - answer: 42
  tasks:
    - name: Display Hello World
      debug:
        msg: "Hello World"
    - name: Display the content of variable answer
      debug:
        var: answer
```
**Modul-Dokumentation:** https://docs.ansible.com/ansible/2.5/modules/debug_module.html

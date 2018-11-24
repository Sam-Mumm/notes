# Codeschnipsel - Linux
## Benutzer und Gruppen
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

---------------------------

## Startscripte

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

# Shell-Befehle

```
- hosts: all
  tasks:
   - name: get kernel version
     command: uname -r
     register: kernel_version

   - name: output kernel version
     debug:
       msg: "On the target kernel {{kernel_version.stdout}} is running"

   - name: Change working dir to /opt/app/init and execute make_db.sh only if /opt/app/db not exists
     command: init/make_db.sh
     args:
       chdir: /opt/app
       creates: /opt/app/database
```

 - **Modul-Dokumentation:** https://docs.ansible.com/ansible/2.5/modules/command_module.html
 - **Notizen:** Ab ansible 2.6 ist es möglich Befehle mit Parametern auch als Liste zu übergeben:
   ```
   - name: Change working dir to /tmp and create the file foo 
     command:
     args:
       chdir: /tmp
       argv:
         - touch
         - foo
   ```
---------------------------

## Startscripte

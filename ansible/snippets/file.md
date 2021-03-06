# Codeschnipsel - Datei Operationen
## Template-Task
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

## Kopieren von Dateien
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

## File-Task
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

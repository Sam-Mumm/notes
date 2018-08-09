# Codeschnipsel
Alle nachfolgenden Codefragmente basieren auf ansible in der Version 2.5

## Dateioperationen
### Template-Task

### Copy-Task
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
**Modul-Documentation: ** https://docs.ansible.com/ansible/2.5/modules/copy_module.html

### File-Task


## Erweiterte Funktionen
### Schleifen-Loop

### Lookups

## sonstiges
### Debug


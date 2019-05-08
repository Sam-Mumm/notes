# Codeschnipsel - Docker
## Starten von einem Docker Container
```
- hosts: all
  tasks:
    - name: create a running container
      docker_container:
        name: testenv
        image: centos:7.6.1810
        state: started
        command: sleep infinity
```
**Modul-Dokumentation:** https://docs.ansible.com/ansible/2.5/modules/docker_container_module.html

## Zugriff auf einen laufenden Container
```
- hosts: all
  tasks:
    - name: add container to inventory
      add_host:
        name: testenv
        ansible_connection: docker

    - name: create file in container
      delegate_to: testenv
      file:
        path: /tmp/testfile
        state: touch
```

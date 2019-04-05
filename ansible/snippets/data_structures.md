# Codeschnipsel - Datenstrukturen 
```
- hosts: all
  vars:
      new_item: "chicken"
      animals:
        - cow
        - duck
        - pig
      users:
        - { name: 'jdoe', group: 'ssh' }
        - { name: 'pmustermann', group: 'user' }
      usernames: []
      server:
        webserver:
          os: Debian
          ip: 192.168.1.1
        database:
          os: CentOS
          ip: 192.168.1.2
  tasks:
    - name: Add string to list
      set_fact:
        animals: '{{ animals + ["dog"] }}'

    - name: Add string from variable to list
      set_fact:
        animals: '{{ animals + [new_item] }}'

    - name: Add List entry to List of Dictionaries
      set_fact:
        users: "{{ users | default([]) + [{'name': 'jperez', 'group': 'www-data'}] }}"

    - name: Covert the Values of the key name to a list
      set_fact:
        usernames: "{{ users | map(attribute='name')|list}}"

    - name: Add dictionary to a list of dictionary
      set_fact:
        server: "{{ server | combine( {'ldap': { 'os': 'SuSE', 'ip': '192.168.1.4' }} ) }}"

```

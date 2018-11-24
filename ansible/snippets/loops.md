# Codeschnipsel - Schleifen
## with_items
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

--------------------------

## with_lines

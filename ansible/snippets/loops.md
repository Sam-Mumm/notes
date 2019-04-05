# Codeschnipsel - Schleifen
## with_items
**Modul-Dokumentation:** https://docs.ansible.com/ansible/2.5/plugins/lookup/items.html

```
- hosts: all
  vars:
    server:
      - webserver
      - database
      - ldap
  tasks:
    - name: Iterate through Variable/Inventory
      debug:
        msg: "Server: {{ function }}"
      with_items: "{{ server }}"
      loop_control:
        loop_var: function
```

--------------------------

## with_lines


--------------------------

## with_dict

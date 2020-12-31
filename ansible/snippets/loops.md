# Codeschnipsel - Schleifen
## Laufvariable
Für jede Schleife lässt sich wie folgt der Name der Laufvariable definieren:
```
loop_control
  loop_var: <Variable_Name>
```

## Schleifentypen
### with_items
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

### with_nested

```
- hosts: all
  vars:
    users:
      - john_doe
      - max_mustermann
      - juan_perez
    permissions:
      - read
      - write
      - admin
  tasks:
    - name: Iterate through Variable/Inventory
      debug:
        msg: "User: {{ item[0] }}, Permission: {{ item[1]  }}"
      with_nested:
        - "{{ users }}"
        - "{{ permissions }}"
```

--------------------------

### with_lines


--------------------------

### with_dict

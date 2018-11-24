# Codeschnipsel - Verschiedenes
## Variable überprüfen
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

----------------------------

## Debug
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

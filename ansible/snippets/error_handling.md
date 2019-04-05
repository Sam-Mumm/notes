# Code Schnipse - Error Handling

## Beenden von einem Playbook forcieren
```
- hosts: all
  tasks:
    - name: Output 1
      debug:
        msg: "Hello World"

    - name: Forced Crash of Playbook
      fail:
        msg: "Something was going wrong"

    - name: Output 2 - will never be reached
      debug:
        msg: "and the whole rest"
```
**Modul-Dokumentation:** https://docs.ansible.com/ansible/2.5/modules/fail_module.html

## try and catch
```
- hosts: all
  tasks:
    - name: Output 1
      debug:
        msg: "Hello World"

    - name: try-block
      block:
        - name: Forced Crash of Playbook
          fail:
            msg: "Something was going wrong"
      rescue:
        - name: Output 2 - will never be reached
          debug:
            msg: "and the whole rest"
      always:
        - name: Output 3 - will always reached
          debug:
            msg: "and thanks for the fish"
```
**Modul-Dokumentation:** https://docs.ansible.com/ansible/2.5/user_guide/playbooks_blocks.html

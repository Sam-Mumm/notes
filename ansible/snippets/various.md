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

----------------------------

## Dialoge
```
- hosts: all
  tasks:
    - name: Paused the playbook
      pause:
        prompt: "Bitte druecken sie eine beliebige Taste zum fortfahren"

    - name: Get new username
      pause:
        prompt: "Bitten geben sie den neuen Benutzernamen ein:"
      register: username

    - name: Get init user password
      pause:
        prompt: "Bitte geben Sie das initiale Passwort ein:"
        echo: no
      register: init_pwd
      no_log: true
```

**Modul-Dokumentation:** https://docs.ansible.com/ansible/2.5/modules/pause_module.html

----------------------------

## Webservices
```
- hosts: all
  tasks:
    - name: Configure SMTP-mailserver
      uri:
        url: http://app.example.com/api/settings
        method: POST
        body: "mail=mail.example.com&port=25"
        user: "admin"
        password: "admin.123"
        status_code: 204
        force_basic_auth: yes
```
**Modul-Dokumentation:** https://docs.ansible.com/ansible/2.5/modules/uri_module.html


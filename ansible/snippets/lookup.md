# Codeschnipsel - Lookup
## Generate Passwords

-----------------


## CSV-Dateien

-----------------

## HashiCorp Vault
**Voraussetzung:** Setzt das Python-Modul *hvac* voraus
```
- hosts: localhost
  vars:
    path_to_secret: "secret/message:value"
    vault_token: "2mDlFNUawn7tDGiTP7hTPCSP"
    vault_server: "https://vaultserver.example.com:8200"
    cacert_path: "/etc/vault/fullchain.pem"
    password: "{{ lookup('hashi_vault', 'secret={{ path_to_secret }} token={{ vault_token }} url={{ vault_server }} cacert={{ cacert_path }}') }}"
  tasks:
    - name: Output Password
      debug:
        var: password

-----------------

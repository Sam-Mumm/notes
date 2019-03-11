# Datenbank
## MySQL
```
- hosts: all
  tasks:
    - name: create a test database
      mysql_db
        name: "test_database"
        state: present
        login_user: "root"
        login_password: "secret_Password!"
        login_host: "127.0.0.1"

    - name: Create a new Datebase-User and give them permission to the database
      mysql_user:
        login_user: "test_user"
        login_password: "test_password123"
        priv: "test_database.*:ALL"      

```
**Modul-Dokumentation:**
- **Datenbanken:** https://docs.ansible.com/ansible/2.5/modules/mysql_db_module.html
- **Benutzer** https://docs.ansible.com/ansible/2.5/modules/mysql_user_module.html

## PostgreSQL
```
- hosts: all
  tasks:
    - name: create a new database
      postgresql_db:$
        name: "test_database"
        login_host: "127.0.0.1"
        login_user: "dbuser"
        login_password: "secret_Password!"
```
**Modul-Dokumentation:**
- **Datenbanken:** https://docs.ansible.com/ansible/2.5/modules/postgresql_db_module.html

# Zugriff auf PostgreSQL

## Abfrage
```
- hosts: all
  vars:
    db_username: "db_user"
    db_password: "secret"
    db_name: "test_database"
    db_host: "localhost"
  tasks:
    - name: "Query"
      postgresql_query
        db: "{{ db_name }}"
        login_host: "{{ db_host }}"
        login_user: "{{ db_username }}"
        login_password: "{{ db_password }}"
        query: "SELECT id, name FROM test_table"  
      register: result

    - name: "Results"
      debug:
        msg: "{{ item.name }}"
      with_items: "{{ result.query_results }}"
```

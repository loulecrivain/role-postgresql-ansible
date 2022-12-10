PostgreSQL role
=========

Deployment automation as an Ansible role for PostgreSQL.

Requirements
------------

Target machine should be Debian/Debian-derived and have a working
apt installation.

Role Variables
--------------

For role variables documentation, please refer to comments in
the variable files.

Example Playbook
----------------

You can use this role as depicted in the following example:
```yaml
    - hosts: db
      roles:
         - role:
           name: postgresql
           vars:
    #       use 25% of total host memory for shared buffers
            postgresql__shared_buffers_percent: 25
            postgresql__databases:
              - { name: 'testdb' }
            postgresql__users:
              - { name: 'testuser', db: 'testdb', password: 'testpassword', comment: 'test user'}
            postgresql__privileges:
              -  {db: 'testdb', privs: 'ALL', role: 'testuser', type: 'database' }
            postgresql__extensions:
              - { name: 'pg_visibility', db: 'testdb', cascade: yes }
```

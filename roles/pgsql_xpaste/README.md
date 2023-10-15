pgsql_xpaste
=========

Role for installation of PostgreSQL on CentOS 7 host. Other OSes are not supported.

Role installs PostgreSQL from standard system repository, initializes, enables and starts the server. Additionally role creates a database and a new user with owner permissions on this database and credentials described in variables.

Requirements
------------

Role actively uses `community.postgres` collection which needs python libraries `psycopg2` and `ipaddress` (these libraries will be installed by role itself).

Role Variables
--------------

|Variable| Default| Description|
|-------------------|--------|--|
| `pgsql_xpaste_pgsql_user` | `xpaste` | This user will be created on server |
| `pgsql_xpaste_pgsql_pass` | `xpaste` | Use password for this user|
| `pgsql_xpaste_database` | `xpaste` | This database will be created and new user will become owner for this DB |

Dependencies
------------

Galaxy roles: `community.postgresql`

Example Playbook
----------------

    ---
    - hosts: shiny_new_pgsql_server
      become: true
      roles:
        - role: pgsql_xpaste
          vars:
            xpaste_database: new_db

License
-------

BSD

Author Information
------------------

Castor Sky (csky57@gmail.com, [Github](https://github.com/castorsky))

xpaste
=========

Role for CentOS7-based deployment of Xpaste service.

Deployment consists of such elements:

* PostgreSQL database (installed with `pgsql_xpaste` role)
* NGINX server as reverse proxy and load balancer (roles `nginxinc.nginx` and `nginxinc.nginx_config`)
* Xpaste server itself (with dependencies: Ruby and NodeJS)

The target server will listen port 80/tcp on all interfaces after deploy. 

Requirements
------------

No special requirements needed.

Role Variables
--------------

All default variables are listed in [defaults/main](defaults/main.yml)

Important variables:

| Variable                   | Default                                    | Description                                                                   |
|----------------------------|--------------------------------------------|-------------------------------------------------------------------------------|
| `xpaste_database_user`     | `xpaste`                                   | PostgreSQL user to create                                                     |
| `xpaste_database_pass`     | `xpaste`                                   | Password for this user                                                        |
| `xpaste_database_name`     | `xpaste`                                   | PostgreSQL database to create and assign owner to user `xpaste_database_user` |
| `xpaste_service_socket`    | `/var/run/puma.sock`                       | Unix socket to use to connect NGINX and Xpaste server                         |
| `xpaste_ruby_version`      | `2.6.10`                                   | Ruby version to in deployment                                                 |
| `xpaste_git_repo_url_base` | `gitlab.slurm.io/edu/xpaste_practicum.git` | Git repo to fetch sources from                                                |
| `xpaste_git_repo_user`     | `git_puller`                               | Git user with repo_read permission                                            |
| `xpaste_git_repo_password` | `**** NO_LOG ****`                         | Git user password                                                             |
| `xpaste_www_root`          | `/var/www`                                 | Web server root directory                                                     |

Dependencies
------------

Role depends on other roles from Galaxy:

- nginxinc.nginx
- nginxinc.nginx_config
- geerlingguy.ruby
- geerlingguy.nodejs

These roles mentioned in requirements.yml and can be installed with

    ansible-galaxy install -r requirements.yml

Example Playbook
----------------

Including an example of how to use your role (for instance, with variables passed in as parameters) is always nice for users too:

    ---
    - hosts: all
      become: true
      gather_facts: true
      gather_subset:
        - min
      roles:
        - role: xpaste
          vars:
            xpaste_git_repo_user: secret_user
            xpaste_git_repo_password: secret_password


License
-------

BSD

Author Information
------------------

Castor Sky (csky57@gmail.com, [Github](https://github.com/castorsky))
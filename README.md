role_app_mysql
=========

Installs a MySQL Server.
This may be a standalone setup or part of a MySQL Master-Slave setup.

TODO
------------

- For Debian 8 and MySQL 5.5 the root password is not reset correctly. Fix manually
Requirements
------------

It expects a system that is set up according to "playbook_baseinstall".

The role "role_mod_repositories" has to be ready in the playbooks ./roles directory.

Role Variables
--------------
The following data structure has to be provided to define the setup:

```
18:22 $ cat group_vars/mysql_cluster/general.yml
role_app_mysql_clusters:
  - name: democluster
    type: master-slave
    hosts:
      - name: master8
        role: master
        repo: distro_default
        version: distro_default
      - name: slave10
        role: slave
        repo: community
        version: "8.0"
```

The MySQL root password is configured through another data structure that is encrypted using ansible-vault:


Dependencies
------------

Used by role_app_acs_mgmt.

Example Playbook
----------------

User by playbook_acs_single_node.

License
-------

GNU Public License v3.0.

Author Information
------------------

Melanie Desaive, m.desaive@mailbox.org

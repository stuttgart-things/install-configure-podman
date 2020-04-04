install-configure-podman
=========

role for installing podman, buildah and skopeo on various os.

Requirements
------------

ansible
centos 7/8; fedora 29+; RHEL7/8; ubuntu 18.04

Role Variables
--------------

A description of the settable variables for this role should go here, including any variables that are in defaults/main.yml, vars/main.yml, and any variables that can/should be set via parameters to the role. Any variables that are read from other roles and/or the global scope (ie. hostvars, group vars, etc.) should be mentioned here as well.

Dependencies
------------

none.

Example Playbook
----------------

```
- hosts: all
  roles:
    - install-configure-podman
```

License
-------

BSD

Author Information
------------------

Patrick Hermann, 04/2020
patrick.hermann@sva.de

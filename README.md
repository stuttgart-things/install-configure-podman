install-configure-podman
=========

role for installing podman, buildah and skopeo on various os.

Requirements
------------

ansible
centos 7/8; fedora 29+; RHEL7/8; ubuntu 18.04

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

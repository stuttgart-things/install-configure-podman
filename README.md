stuttgart-things/install-configure-podman
=========================================

role for installing podman, buildah and skopeo on various os.

## Step 1: Install ansible requirements

copy and paste the following into your terminal:

```
cat <<EOF > /tmp/requirements.yaml
- src: git@codehub.sva.de:Lab/stuttgart-things/supporting-roles/install-configure-podman.git
  version: stable
  scm: git
- src: git@codehub.sva.de:Lab/stuttgart-things/supporting-roles/install-requirements.git
  version: stable
  scm: git
collections:
- name: community.general
  version: 1.3.2
EOF
ansible-galaxy install -r /tmp/requirements.yaml --force
rm -rf /tmp/requirements.yaml
```

## Step 2: define & run playbook 

copy and paste the following (on any place of the filesystem of the ansible host) into your terminal:

```
cat <<EOF > install-configure-podman.yaml
---
- hosts: "{{ target_host }}"
  become: true
  roles:
    - role: install-configure-podman
EOF 
```

Execute playbook:
```
ansible-playbook -i my_inventory install-configure-podman.yaml -vv 
```

Role history
----------------
| date  | who | changelog |
|---|---|---|
|2020-04-03  | Patrick Hermann | intial commit for this role on codehub
|2020-10-10  | Patrick Hermann | Updated for using ansible collections, added Debian support; defined stable version

License
-------

BSD

Author Information
------------------

Patrick Hermann (patrick.hermann@sva.de); 04/2020
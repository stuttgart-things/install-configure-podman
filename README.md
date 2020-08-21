install-configure-podman
=========

role for installing podman, buildah and skopeo on various os.

## Step 1: Install ansible requirements

<details><summary><textb> Install requirements (expand for details) </textb></summary>

copy and paste the following into your terminal
```
cat <<EOF > /tmp/requirements.yaml
- src: git@codehub.sva.de:Lab/stuttgart-things/supporting-roles/install-configure-podman.git
  scm: git
EOF
ansible-galaxy install -r /tmp/requirements.yaml --force
rm -rf /tmp/requirements.yaml
```
</details>

## Step 2: define & run playbook 

<details><summary><textb> Example playbook (expand for details) </textb></summary>

copy and paste the following (on any place of the filesystem of the ansible host) into your terminal:
```
---
cat <<EOF > install-configure-podman.yaml
- hosts: all 

  roles:
    - role: install-configure-podman
EOF 
```

Execute playbook:
```
ansible-playbook install-configure-podman.yaml -vv 
```

</details>


License
-------

BSD

Author Information
------------------

Patrick Hermann, 04/2020
patrick.hermann@sva.de

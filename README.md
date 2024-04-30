stuttgart-things/install-configure-podman
=========================================

installs and configures podman, buildah and skopeo on various linux os

<details><summary>Variables</summary>

* `install_tools` -  Set this on False if you don't want buildah and skopeo to be installed (default: true)
* `buildah_version` - Set the wanted buildah version
* `skopeo_version` -  Set the wanted skopeo version
* `configure_docker_registry_mirror` -  Set this on true if you want docker registry mirrors to be created (default: false)
* `ubuntu_version` -  If you don't use a different OS, set your Ubuntu version

</details>

<details><summary>ROLE INSTALLATION</summary>

copy and paste the following into your terminal:

```bash
cat <<EOF > /tmp/requirements.yaml
roles:
- src: https://github.com/stuttgart-things/install-configure-podman.git
  scm: git
- src: https://github.com/stuttgart-things/install-requirements.git
  scm: git

collections:
- name: community.general
  version: 8.6.0
- name: containers.podman
  version: 1.13.0
EOF

ansible-galaxy install -r /tmp/requirements.yaml --force
ansible-galaxy collection install -r /tmp/requirements.yaml --force

rm -rf /tmp/requirements.yaml
```

</details>

<details><summary>EXAMPLE INVENTORY</summary>

```bash
cat <<EOF > inventory
[appserver]
1.2.3.4 ansible_user=sthings
EOF
```

</details>

<details><summary>EXAMPLE PLAYBOOK</summary>

copy and paste the following (on any place of the filesystem of the ansible host) into your terminal:

```yaml
cat <<EOF > install-configure-podman.yaml
---
- hosts: "{{ target_host | default('all') }}"
  become: true
  roles:
    - role: install-configure-podman
EOF 
```

<details><summary>EXAMPLE EXECUTION</summary>

```bash
ansible-playbook -i inventory install-configure-podman.yaml -vv 
```

</details>

<details><summary>EXAMPLE USE-CASES BUILDAH</summary>

```bash
# Check buildah version
buildah version
```
```bash
# Pull Image
sudo buildah pull alpine
```
```bash
# Show Image
sudo buildah images
```
```bash
# Create Container
sudo buildah from docker.io/library/alpine
```
```bash
# Show Container
sudo buildah containers
```

</details>

<details><summary>EXAMPLE USE-CASES SKOPEO</summary>

```bash
# Login to private registry with authentication
skopeo login --username USER myregistrydomain.com:5000
# Logout of private registry
skopeo logout myregistrydomain.com:5000
```
```bash
# Show properties of docker.io/library/alpine
skopeo inspect docker://docker.io/library/alpine
```
```bash
# Syncing registries
skopeo sync --src docker --dest dir registry.example.com/busybox /media/usb
```
```bash
# Copy Image
skopeo copy oci:busybox_ocilayout:latest dir:existingemptydirectory
# Copy Image with creds
skopeo copy --src-creds=testuser:testpassword docker://myregistrydomain.com:5000/private oci:local_oci_image
```

</details>

## License
<details><summary>LICENSE</summary>

Copyright 2020 patrick hermann.

Licensed under the Apache License, Version 2.0 (the "License");
you may not use this file except in compliance with the License.
You may obtain a copy of the License at

    http://www.apache.org/licenses/LICENSE-2.0

Unless required by applicable law or agreed to in writing, software
distributed under the License is distributed on an "AS IS" BASIS,
WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
See the License for the specific language governing permissions and
limitations under the License.

</details>

Role history
----------------
| date  | who | changelog |
|---|---|---|
|2023-30-04  | Andre Ebert | Added Buildah and Skopeo install, added linting and skip rules and workflows
|2020-10-10  | Patrick Hermann | Updated for using ansible collections, added Debian support; defined stable version
|2020-04-03  | Patrick Hermann | intial commit for this role on codehub

Author Information
------------------

```yaml
Andre Ebert (andre.ebert@sva.de); 04/2023

Patrick Hermann (patrick.hermann@sva.de); Stuttgart-Things; 04/2020
```

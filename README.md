# ansible-role-docker

![GitHub](https://img.shields.io/github/license/jam82/ansible-role-docker) ![GitHub last commit](https://img.shields.io/github/last-commit/jam82/ansible-role-docker) ![GitHub issues](https://img.shields.io/github/issues-raw/jam82/ansible-role-docker) ![Travis (.com) branch](https://img.shields.io/travis/com/jam82/ansible-role-docker/main?label=travis) [![Molecule](https://github.com/jam82/ansible-role-docker/actions/workflows/molecule.yml/badge.svg)](https://github.com/jam82/ansible-role-docker/actions/workflows/molecule.yml)

**Ansible role for setting up Docker from OS Repositories.**

For installing official Docker CE use another role, e.g. from

- [geerlingguy/ansible-role-docker](https://github.com/geerlingguy/ansible-role-docker)

This role installs the following packages:

- docker
- docker python libraries
- fuse-overlayfs

Optionally you can install `docker-compose`
and set configuration options for `/etc/docker/daemon.json`, as storage drivers (btrfs, dm, zfs,), etc...

## Supported Platforms

| OS Family | Distribution  | Latest | Supported Version(s) | Comment |
|-----------|---------------|--------|----------------------|---------|
| Alpine    | Alpine        | :heavy_check_mark: | 3.12, 3.13 | |
| Archlinux | Archlinux     | :heavy_check_mark: | - | |
|           | Manjaro       | :heavy_check_mark: | - | |
| Debian    | Debian        | :heavy_check_mark: | 10, 11 | |
|           | Ubuntu        | :heavy_check_mark: | 18.04, 20.04 | |
| RedHat    | Fedora        | :heavy_check_mark: | 33, 34, Rawhide | |
| Suse      | OpenSuse Leap | :heavy_check_mark: | 15.1, 15.2, 15.3 | |
|           | Tumbleweed    | :heavy_check_mark: | - | |

## Requirements

Ansible 2.9 or higher.

## Variables

Variables and defaults for this role.

### defaults/main.yml

```yaml
---
# role: ansible-role-docker
# file: defaults/main.yml

# The role is disabled by default, so you do not get in trouble.
# Checked in tasks/main.yml which includes tasks/tasks.yml if enabled.
docker_role_enabled: false

# install docker compose.
docker_compose: false

# Docker daemon configuration. Write the config as dict in YAML notation.
# It will be converted to JSON by the template.
# see https://docs.docker.com/engine/reference/commandline/dockerd/#daemon-configuration-file
# EXAMPLE:
# docker_daemon:
#   "storage-driver": "btrfs"
#   "storage-opts":
#     - "btrfs.min_space": "1G"
docker_daemon: {}
```

## Dependencies

None.

## Example Playbook

```yaml
---
# role: ansible-role-docker
# play: docker
# file: docker.yml

- hosts: all
  become: true
  gather_facts: true
  vars:
    docker_role_enabled: true
  roles:
    - role: ansible-role-docker
```

## License and Author

- Author:: [jam82](https://github.com/jam82/)
- Copyright:: 2021, [jam82](https://github.com/jam82/)

Licensed under [MIT License](https://opensource.org/licenses/MIT).
See [LICENSE](https://github.com/jam82/ansible-role-docker/blob/master/LICENSE) file in repository.

## References

- [ArchWiki](https://wiki.archlinux.org/)

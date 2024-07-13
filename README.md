# Ansible role [docker_ce](https://galaxy.ansible.com/ui/standalone/roles/buluma/docker_ce/documentation)

Install and configure Docker CE on your system.

|GitHub|Version|Issues|Pull Requests|Downloads|
|------|-------|------|-------------|---------|
|[![github](https://github.com/buluma/ansible-role-docker_ce/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-docker_ce/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-docker_ce.svg)](https://github.com/buluma/ansible-role-docker_ce/releases/)|[![Issues](https://img.shields.io/github/issues/buluma/ansible-role-docker_ce.svg)](https://github.com/buluma/ansible-role-docker_ce/issues/)|[![PullRequests](https://img.shields.io/github/issues-pr-closed-raw/buluma/ansible-role-docker_ce.svg)](https://github.com/buluma/ansible-role-docker_ce/pulls/)|[![Ansible Role](https://img.shields.io/ansible/role/d/buluma/docker_ce)](https://galaxy.ansible.com/ui/standalone/roles/buluma/docker_ce/documentation)|

## [Example Playbook](#example-playbook)

This example is taken from [`molecule/default/converge.yml`](https://github.com/buluma/ansible-role-docker_ce/blob/master/molecule/default/converge.yml) and is tested on each push, pull request and release.

```yaml
---
- name: Converge
  hosts: all
  become: yes
  gather_facts: yes

  roles:
    - role: buluma.docker_ce
      docker_ce_privileged_users:
        - woody
        - buzz
```

The machine needs to be prepared. In CI this is done using [`molecule/default/prepare.yml`](https://github.com/buluma/ansible-role-docker_ce/blob/master/molecule/default/prepare.yml):

```yaml
---
- name: Prepare
  hosts: all
  gather_facts: no
  become: yes

  roles:
    - role: buluma.bootstrap
    - role: buluma.epel
    - role: buluma.buildtools
    - role: buluma.python_pip
    - role: buluma.core_dependencies

  tasks:
    - name: Create test case users
      ansible.builtin.user:
        name: "{{ user }}"
      loop:
        - woody
        - buzz
      loop_control:
        loop_var: user
```

Also see a [full explanation and example](https://buluma.github.io/how-to-use-these-roles.html) on how to use these roles.

## [Role Variables](#role-variables)

The default values for the variables are set in [`defaults/main.yml`](https://github.com/buluma/ansible-role-docker_ce/blob/master/defaults/main.yml):

```yaml
---
# defaults file for docker_ce

# Add users to the privileged docker group. For example:
# docker_ce_privileged_users:
#  - UserA
#  - UserB
docker_ce_privileged_users: []
```

## [Requirements](#requirements)

- pip packages listed in [requirements.txt](https://github.com/buluma/ansible-role-docker_ce/blob/master/requirements.txt).

## [State of used roles](#state-of-used-roles)

The following roles are used to prepare a system. You can prepare your system in another way.

| Requirement | GitHub | Version |
|-------------|--------|--------|
|[buluma.bootstrap](https://galaxy.ansible.com/buluma/bootstrap)|[![Ansible Molecule](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-bootstrap/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-bootstrap.svg)](https://github.com/shadowwalker/ansible-role-bootstrap)|
|[buluma.buildtools](https://galaxy.ansible.com/buluma/buildtools)|[![Ansible Molecule](https://github.com/buluma/ansible-role-buildtools/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-buildtools/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-buildtools.svg)](https://github.com/shadowwalker/ansible-role-buildtools)|
|[buluma.core_dependencies](https://galaxy.ansible.com/buluma/core_dependencies)|[![Ansible Molecule](https://github.com/buluma/ansible-role-core_dependencies/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-core_dependencies/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-core_dependencies.svg)](https://github.com/shadowwalker/ansible-role-core_dependencies)|
|[buluma.epel](https://galaxy.ansible.com/buluma/epel)|[![Ansible Molecule](https://github.com/buluma/ansible-role-epel/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-epel/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-epel.svg)](https://github.com/shadowwalker/ansible-role-epel)|
|[buluma.python_pip](https://galaxy.ansible.com/buluma/python_pip)|[![Ansible Molecule](https://github.com/buluma/ansible-role-python_pip/actions/workflows/molecule.yml/badge.svg)](https://github.com/buluma/ansible-role-python_pip/actions/workflows/molecule.yml)|[![Version](https://img.shields.io/github/release/buluma/ansible-role-python_pip.svg)](https://github.com/shadowwalker/ansible-role-python_pip)|

## [Context](#context)

This role is a part of many compatible roles. Have a look at [the documentation of these roles](https://buluma.github.io/) for further information.

Here is an overview of related roles:

![dependencies](https://raw.githubusercontent.com/buluma/ansible-role-docker_ce/png/requirements.png "Dependencies")

## [Compatibility](#compatibility)

This role has been tested on these [container images](https://hub.docker.com/u/buluma):

|container|tags|
|---------|----|
|[Debian](https://hub.docker.com/r/buluma/debian)|bullseye|
|[EL](https://hub.docker.com/r/buluma/enterpriselinux)|9|
|[Fedora](https://hub.docker.com/r/buluma/fedora)|39, 38, 40|
|[Ubuntu](https://hub.docker.com/r/buluma/ubuntu)|jammy, focal, bionic, noble, lunar|

The minimum version of Ansible required is 2.12, tests have been done to:

- The previous version.
- The current version.
- The development version.

If you find issues, please register them in [GitHub](https://github.com/buluma/ansible-role-docker_ce/issues)

## [Changelog](#changelog)

[Role History](https://github.com/buluma/ansible-role-docker_ce/blob/master/CHANGELOG.md)

## [License](#license)

[Apache-2.0](https://github.com/buluma/ansible-role-docker_ce/blob/master/LICENSE)

## [Author Information](#author-information)

[Shadow Walker](https://buluma.github.io/)

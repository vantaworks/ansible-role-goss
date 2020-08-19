Goss Ansible Role
==================

[![Build Status](https://travis-ci.com/vantaworks/ansible-role-goss.svg?branch=master)](https://travis-ci.com/vantaworks/ansible-role-goss)

A simple Ansible role to install [goss](https://github.com/aelsabbahy/goss).

Requirements
------------
None. The [goss](https://github.com/aelsabbahy/goss) binary is self contained.

Install
-------
To install directly from GitHub
```
- name: goss
  src: http://github.com/vantaworks/goss.git
  scm: git
  version: master
```

Or, if you want to install from [Ansible Galaxy](https://galaxy.ansible.com/vantaworks/goss):
```
- name: goss
  src: vantaworks.goss
  version: master
```

Then run the following tocmmand to install.
```
ansible-galaxy install -p roles -r requirements.yml -f
```

Further information on [variables](#role-variables) and [example playbooks](#example-playbooks) are shown below.


Role Variables
--------------
Available variables are listed below, along with default values (see `defaults/main.yml`):

Whether or not you want to install or uninstall `goss`
```
goss_state: "present"
goss_state: "absent"
```

Whether or not you want to override/upgrade the version already installed.
```
goss_force_reinstall: True
```

Specify a specific version of `goss` to install. __Recommended:__ Leave this blank so the newest is used.
```
goss_version: 0.3.13
```

Which URL to use as the source-of-truth for `goss` versions.
```
goss_version_url: "https://api.github.com/repos/aelsabbahy/goss/tags?per_page=300"
```

Where to donload the `goss` binary from?
```
goss_download_url: "https://github.com/aelsabbahy/goss/releases/download/{{ goss_version }}/goss-linux-{{ goss_arch }}"
```

What is the intended architecture?
```
goss_arch: amd64
# options include: amd64, 386, and arm
```

Where should `goss` be installed to?
```
goss_install_path: /usr/local/bin/goss
```

Dependencies
------------
No Ansible-Python dependencies. See [Requirements](#requirements) above for role requirements.

Example Playbooks
-----------------
```
# Install the latest `goss` verison
- name: Example Install Play 1
  hosts: goss
  roles:
    - vantaworks.goss

# Install a specified `goss` version
- name: Example Install Play 2
  hosts: goss
  vars:
    goss_version: 0.3.13
  roles:
    - vantaworks.goss

# Uninstall `goss`
- name: Example Uninstall Play
  hosts: goss
  vars:
    goss_state: "absent"
  roles:
    - vantaworks.goss
```

License
-------

BSD

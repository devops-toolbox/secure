Role Name
=========

secure: Secure

[![Build Status](https://travis-ci.org/cmihai-ansible/secure.svg?branch=master)](https://travis-ci.org/cmihai-ansible/secure)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devopstoolbox.secure](https://galaxy.ansible.com/devopstoolbox.secure)

```bash
ansible-galaxy install devopstoolbox.secure
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
secure_packages_state: present
secure_remove_packages: true
secure_enable_service: true
secure_enable_selinux: true
secure_copy_templates: true
secure_firewall_configure: true
secure_firewall_rules:
  - service: ssh
  - port: 3389
secure_users:
  - user: devops
    group: docker
secure_selinux_booleans:
  - name: ftp_home_dir
    state: true
    persistent: true
```

Dependencies
------------

- For Red Hat, subscription-manager.

Example Playbook
----------------

```yaml
---
- name: Install secure on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: secure is configured
      import_role:
        name: devopstoolbox.secure
      vars:
        secure_packages_state: present
        secure_remove_packages: true
        secure_enable_service: true
        secure_enable_selinux: true
        secure_copy_templates: true
        secure_firewall_configure: true
        secure_firewall_rules:
          - service: ssh
          - port: 3389
        secure_users:
          - user: devops
            group: docker
        secure_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: secure
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devopstoolbox.)

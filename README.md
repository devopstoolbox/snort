Role Name
=========

snort: Snort

[![Build Status](https://travis-ci.org/cmihai-ansible/snort.svg?branch=master)](https://travis-ci.org/cmihai-ansible/snort)

Ansible galaxy:
---------------

[https://galaxy.ansible.com/devops-toolbox.snort](https://galaxy.ansible.com/devops-toolbox.snort)

```bash
ansible-galaxy install devops-toolbox.snort
```

Requirements
------------

- For RHEL, a Red Hat subscription or functional local repository.
- Ansible 2.4 or higher

Role Variables
--------------

```yaml
snort_packages_state: present
snort_remove_packages: true
snort_enable_service: true
snort_enable_selinux: true
snort_copy_templates: true
snort_firewall_configure: true
snort_firewall_rules:
  - service: ssh
  - port: 3389
snort_users:
  - user: devops
    group: docker
snort_selinux_booleans:
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
- name: Install snort on localhost
  hosts:
    - localhost
  connection: local

  tasks:
    - name: snort is configured
      import_role:
        name: devops-toolbox.snort
      vars:
        snort_packages_state: present
        snort_remove_packages: true
        snort_enable_service: true
        snort_enable_selinux: true
        snort_copy_templates: true
        snort_firewall_configure: true
        snort_firewall_rules:
          - service: ssh
          - port: 3389
        snort_users:
          - user: devops
            group: docker
        snort_selinux_booleans:
          - name: ftp_home_dir
            state: true
            persistent: true
      tags: snort
```

License
-------

MIT

Author Information
------------------

- [Mihai Criveti](https://www.linkedin.com/in/devops-toolbox.)
